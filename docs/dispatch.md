# GHA dispatch イベント

  GithubActions にて dispatch イベントを使用することで、 workflow をAPIで動かすことができる

## GithubActions側

```
on:
  repository_dispatch:
    types: [hello]
```

`types` を指定することで、フィルタリングを行うことができる。

## 呼び出し側

`curl` などを使用することでTerminalなどから呼び出すことができる。

```
$ curl -X POST -H "Authorization: token $TOKEN" -H "Accept: application/vnd.github.everest-preview+json" https://api.github.com/repos/chihirof/GHA_dispatch_receive/dispatches -d '{"event_type":"hello"}'
```

`-X` : Method指定  
`-H` : リクエストヘッダー指定  
`-d` : データ  

`-d '{"event_type":"hello"}'` について  
- `event_type` は必須項目
- `client_payload` を指定することで、そのほかのデータを送ることができる。JSON。


## GHA コンテキスト情報へのアクセス

https://help.github.com/ja/actions/reference/context-and-expression-syntax-for-github-actions#github-context




## 参考

- https://help.github.com/en/actions/reference/events-that-trigger-workflows#external-events-repository_dispatch
- https://developer.github.com/v3/repos/#create-a-repository-dispatch-event
- https://qiita.com/ryuichi1208/items/e4e1b27ff7d54a66dcd9
