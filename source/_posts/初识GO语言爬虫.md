---
title: 初识GO爬虫
date: 2024-04-27 21:46:29
tags:
  - 爬虫
categories:
  - GO

---

# 初识 GO 语言爬虫

## 基本思路

- 明确所需爬取的内容
- 分析页面信息
- 获取页面信息
- 解析页面信息

## 获取页面信息

使用**http** 库发送请求，使用GO的 net/http 用来发送HTTP请求。在发送请求之前还需要将请求模拟成客户端请求。

**创建请求:** 

```go
// url.Values 用于构建和解析 url 中的查询参数
values := url.Values{}
values.Add([key], [value])

// 新建一个请求
req, err := http.NewRequest([method], [url], strings.NewReader(values.Encode()))
if err != nil {
  panic(err)
}

// 模拟客户端请求头
req.Header.Set("User-Agent", "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/124.0.0.0 Safari/537.36")
```



**模拟客户端: **

```go
// 模拟客户端
client := &http.client{}

// 请求url地址
resp, err := client.Do(req)
if err != nil {
  panic(err)
}

defer resp.Body.Close()

body, err := io.ReadAll(resp.Body)
if err != nil {
  panic(err)
}

// 响应码
fmt.Println("Rsponse Status Code: ", resq.StatusCode)
// 响应信息
fmt.Println("Rsponse Body: ", string(body))

```

## 解析页面信息

将获取到的内容进行解析，可以使用 **goquery**库帮忙，可以通过像Jquery一样更方便获取元素信息以便使用

```go
// 通过 goquery 库的NewDocumentFromReader 解析 resq.Body
doc, err := goquery.NewDocumentFromReader(resq.Body)
if err != nil {
  panic(err)
}

// 通过Jquery的方式获取doc元素
doc.Find("JQ选择器").Each(func(i int, s *goquery.Selection){
  content := s.Text()
  fmt.Println("content", content)
}
```

**将解析的图片保存到本地: **

```go
doc.Find("JQ选择器 img").Each(func(i int, s *goquery.Selection){
  imgSrc, exitis := s.Attr("src")
  if exitis {
    // 获取图片路径
    imgResp, err := http.Get(imgSrc)
    if err != nil {
      panic(err)
    }
    defer imgResp.Body.Close()
    
    // 将文本写入文件
    imgFileName, err := "img_" +  strconv.Itoa(i) + ".png"
    file, err := os.Create(imgFileName)
    if err != nil {
      panic(err)
    }
    defer file.Close()
    _, err = io.Copy(file, imgSrc.Body)
    if err != nil {
      panic(err)
    }
  }
}
```





## 并发与限流

避免过度请求导致对目标服务器的负载过重或被封禁，可以使用 Go 的并发控制以及 `time.Tick` 或第三方限流库来实现。

## 链接提取与遍历

需要实现一定的逻辑来提取页面中的链接，并决定哪些链接会被进一步跟踪和抓取。

## 数据存储

抓取的数据需要被存储以供后续使用，可以使用文件、数据库或者其他存储方式。
