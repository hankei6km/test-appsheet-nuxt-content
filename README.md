# appsheet-to-nuxt-content

Save contents from [AppSheet](https://www.appsheet.com/) for use within  [nuxt-content](https://content.nuxtjs.org/).

## AppSheet settings

### Application

- Open "Manage" / "Integrations" / "IN: from cloud services to your app"
- Turn on "Enable"
- Generate access key by "Create Application Access Key"

refer: [API: The Essentials | AppSheet Help Center](https://help.appsheet.com/en/articles/1979966-api-the-essentials)

### Image
(It require when using image)

- Open "Security" / "Options"
- Turn off "Require Image and File URL Signing"

refer: [Displaying Images and Documents | AppSheet Help Center](https://help.appsheet.com/en/articles/961605-displaying-images-and-documents)


## Local settings

### Column map

- `mapcol.json(sample)`

```json
[
    {
        "srcName": "タイトル",
        "dstName": "title",
        "colType": "string"
    },
    {
        "srcName": "画像",
        "dstName": "image",
        "colType": "image"
    }
]
```

### Env variables

- `sample`

```
SHEET2CONTENT_API_BASE_URL=https://api.appsheet.com/api/v2/
SHEET2CONTENT_APP_ID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx
SHEET2CONTENT_APP_NAME=<app name>-xxxxxxx
SHEET2CONTENT_MAP_COLS=path/to/mapcols.json
SHEET2CONTENT_ACCESS_KEY=xx-xxxxx-xxxxx-xxxxx-xxxxx-xxxxx-xxxxx-xxxxx-xxxxx
```


## Save contents

```bash
npx --package=appsheet-to-nuxt-content -c \
  'sheet2content save <table name> <contents dir> <iamges dir>'
```

## API

### `client(apiBaseURL, appId, appName, accessKey)`

Return client instance for AppSheet. 

#### `apiBaseURL`

Base URL to API endpoint.

#### `appId`

App Id to API endpoint.

#### `appName`

App Name to image adapter endpoint.

#### `accessKey`

Access key to get contents.

#### returns

`Client`
 

### `saveRemoteContents(client, tableName, mapCols, dstContentDir, dstImagesDir)`

Save remote contens.

#### `client`

AppSheet client.

#### `tableName`

Table name to save contents.

##### `mapCols`

Colmuns map.

##### `dstContentDir`
 
directory to save contents.

##### `dstImagesDir`
 
directory to save images.

#### returns

`Promise<Error | null>`


## License

MIT License

Copyright (c) 2021 hankei6km

