# dockerfile



## gobuild
> 用來建置 go image 使用

```shell
    docker build --build-arg COMMIT=$COMMIT \
                 --build-arg DATE=$DATE \
                 --build-arg TAG=$TAG \
                 --force-rm \
                 -t"$REGISTRY":"$TAG" .
```

### 參數說明
|參數名稱|說明|
|---|---|
|$COMMIT|git commit 編號|
|$DATE | 建置時間|
|$TAG| 部屬版本|
|$REGISTRY| Image 名稱|

> $REGISTRY 預設為 : registry.gitlab.com/axolotl.team/{專案群組名稱}/{專案名稱}/deploy/{服務名稱}
