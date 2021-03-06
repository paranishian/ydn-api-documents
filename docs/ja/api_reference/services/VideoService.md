# VideoService
VideoServiceでは、動画入稿に関する機能を提供します。

#### WSDL
| environment | url |
|---|---|
| production  | https://location.im.yahooapis.jp/services/V201809/VideoService?wsdl|
| sandbox  | https://sandbox.im.yahooapis.jp/services/V201809/VideoService?wsdl|

#### Namespace
http://im.yahooapis.jp/V201809/Video

#### サービス概要
動画入稿に関する情報の取得、および動画のアップロード、ダウンロード、変更、削除を行います。

#### 操作
VideoServiceで提供される操作を説明します。

+ [get](#get)
+ [getUploadUrl](#getuploadurl)
+ [upload](#upload)
+ [mutate(SET)](#mutateset)
+ [mutate(REMOVE)](#mutateremove)

#### オブジェクト
[Video](../data/Video)

## get

### リクエスト
入稿済の動画の情報を取得します。

| パラメータ | 必須 | データ型 | 説明 |
|---|---|---|---|
| selector | ○ | [VideoSelector](../data/Video/VideoSelector.md) | 動画の情報を取得します。 |

##### ＜リクエストサンプル＞
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header>
    <RequestHeader xmlns="http://im.yahooapis.jp/V201809/Video" xmlns:ns2="http://im.yahooapis.jp/V201809">
      <ns2:license>1111-1111-1111-1111</ns2:license>
      <ns2:apiAccountId>2222-2222-2222-2222</ns2:apiAccountId>
      <ns2:apiAccountPassword>password</ns2:apiAccountPassword>
    </RequestHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <get xmlns="http://im.yahooapis.jp/V201809/Video" xmlns:ns2="http://im.yahooapis.jp/V201809">
      <selector>
        <accountId>1111</accountId>
        <mediaIds>2222</mediaIds>
        <mediaIds>3333</mediaIds>
        <userStatuses>ACTIVE</userStatuses>
        <userStatuses>PAUSED</userStatuses>
        <approvalStatuses>APPROVED</approvalStatuses>
        <approvalStatuses>REVIEW</approvalStatuses>
        <approvalStatuses>PRE_DISAPPROVED</approvalStatuses>
        <approvalStatuses>POST_DISAPPROVED</approvalStatuses>
        <paging>
          <ns2:startIndex>1</ns2:startIndex>
          <ns2:numberResults>10</ns2:numberResults>
        </paging>
      </selector>
    </get>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### レスポンス
| フィールド | データ型 | 説明 |
|---|---|---|
| rval | [VideoPage](../data/Video/VideoPage.md) | 操作結果を表示します。 |

##### ＜レスポンスサンプル＞
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header>
    <ResponseHeader xmlns="http://im.yahooapis.jp/V201809/Video" xmlns:ns2="http://im.yahooapis.jp/V201809">
      <ns2:service>Video</ns2:service>
      <ns2:requestTime>1536568330374</ns2:requestTime>
      <ns2:timeTakenSeconds>0.2671</ns2:timeTakenSeconds>
    </ResponseHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <ns2:getResponse xmlns="http://im.yahooapis.jp/V201809" xmlns:ns2="http://im.yahooapis.jp/V201809/Video">
      <ns2:rval>
        <totalNumEntries>1</totalNumEntries>
        <Page.Type>VideoPage</Page.Type>
        <ns2:values>
          <operationSucceeded>true</operationSucceeded>
          <ns2:video>
            <ns2:accountId>1111</ns2:accountId>
            <ns2:mediaId>2222</ns2:mediaId>
            <ns2:videoName>tes</ns2:videoName>
            <ns2:videoTitle>tes2</ns2:videoTitle>
            <ns2:userStatus>ACTIVE</ns2:userStatus>
            <ns2:creationTime>20171024175716</ns2:creationTime>
            <ns2:approvalStatus>REVIEW</ns2:approvalStatus>
            <ns2:processStatus>FINISHED</ns2:processStatus>
            <ns2:videoSetting>
              <ns2:videoFileType>MP4</ns2:videoFileType>
              <ns2:videoAdFormat>YJ_640_360</ns2:videoAdFormat>
              <ns2:fileSize>29672732</ns2:fileSize>
              <ns2:width>640</ns2:width>
              <ns2:height>360</ns2:height>
              <ns2:playbackTime>60</ns2:playbackTime>
              <ns2:downloadOriginalUrl>https://colo01.im.yahooapis.jp/video/V201809/download/viZdXh.JqONCS1dU.dwWmnpIy_ITbPW2ahEb6ze_pZ4FID.XPbYHQc4zOEioYE7jhuJbrwX5QIcVv9H0cqQVszlNOzOY9aTuS1XYe7GUZhSasUj0tl2s1TWgbgxWmB004XRVt9FizVW_HXQgyYwgRjYJPQPqw4lcvbF1Vcf_UE8uLwhWwfbGjkkwwNIzbsDdLIceGTFbx7IiowQ9a73hWWArnvCbFWmBD.FN7HYd2FTGLoXKzcYZSDbMRMIs7HPkn4UvKqi_xLqKg_.33Ri0BmwfqhCnB7W2poxqddU8l15tMltkShxGURZ7zcdB.fwL1Q1KBmiltHhl6.0094X_HM.VLZjKAIhs4qiKLt9NMkpvL0bCygZHETuWkoIQZsg-</ns2:downloadOriginalUrl>
              <ns2:downloadHighBitrateUrl>https://colo01.im.yahooapis.jp/video/V201809/download/rwEr8wyJqOOhXYR9yKYWF3oViR5FAeebem9bEE72WgNqkhrVY4Bwfv6_1Yb6FrxOJcb9yXskjrcRwCEqHzqxOG_.8J4quw37bE0rleZHzh84Q1bAGwKUck3p70sWjOPopu1rcOJurCoo3.jhaHZVRQOGNFO7_HPJAeHEyN19IKjbBnIYFkZMatpHWTr20scfbJDt6AD0sE658RHSoNRSSj7XKxcawCw4seE9wsEQgGNwpNM2Y_ARzu3qURQOXya0J3LInGw0Cy_Jrg.ibPsf20ITAOhwX6tl8OyhcbSI1tHjUVIFxupeOImlJxtq8lDlYCPnleIHfGcNmrGXb7Our2rpT4POwzMXlc3YF4MrSI4XySxZpys3ZJe6Q6QEDFpz_Q--</ns2:downloadHighBitrateUrl>
              <ns2:downloadMiddleBitrateUrl>https://colo01.im.yahooapis.jp/video/V201809/download/vQRhca.JqOOhBifcqXbbRZlJOt1X9.v_2rNkYgSO71R03bXBDyBU5QoEm.O83ugEK9KTvFtFs6KU9bxBhqBwD8yzbNcP2euqi7wIkEfNY3OaQmYIVYFBi0dWq6aVUJwZPLepILE0vEJbNBpEuYCAq1r2Lk.wsG_QRgXZ3JTmuay58jYSjhc.v67VSBGvIHEZqYwdlr34Fuh7JwmBk0onAKVJL4bbghxXYlJH4x6C7Z9gBMlUkaVAEg9NEjoBwHOWbRLxC9SZ6acAc1Jv8z71OJ2dLu.NTIj2VPeGK35e4ogX8qI_HRFIjfZW_tT3Z3u..BpWQ6f0vc.NS1paxaoMU0BX8Dq.qIUFtRhuHEs9N0R3lQeswgbfQGz_qtr5</ns2:downloadMiddleBitrateUrl>
              <ns2:downloadLowBitrateUrl>video/V201809/download/vk88mJeJqON_XBRyO53kY9OWNrTQzPGAPZV2tklh5eqPV2nmecFPiOUoVl50VmnLSf8a2vCCp6TRX1iRRfFbfn8zQcYHwPu.clnL.ZFa1goVi9HnaNW9gi14xHfGUJV3WjRkhza8eBmL0_1.sN4P0odwRV2oRQCfGhuFL9jUK5oPNfNlmYV3F2gNEvDD.Lps8pDIuqIKSGVqH7.0kXrR.bU0Stvp_rkYBXTRLjDgi6YGgL96H0dlCF5aHEDnM.f6vKIq0qFxwRAWAWcz166YhTO8jYV9._QF_5z1e0nzMpeuQVZCXTf5UAU8eZDqhMXIvs7ztUfd1L5_6YJeTBm2Z34lF.m1WGrTlFmBHBFco5_2USOWKoz2cE4gGtVOA5c-</ns2:downloadLowBitrateUrl>
            </ns2:videoSetting>
          </ns2:video>
        </ns2:values>
      </ns2:rval>
    </ns2:getResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## getUploadUrl
動画アップロード用URLを取得します。

### リクエスト
| パラメータ | 必須 | データ型 | 説明 |
|---|---|---|---|
| accountId | ○ | long | アカウントIDです。 |
| uploadVideo | ○ | [UploadVideo](../data/Video/UploadVideo.md) | アップロードする動画の情報です。 |

##### ＜リクエストサンプル＞
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header>
    <RequestHeader xmlns="http://im.yahooapis.jp/V201809/Video" xmlns:ns2="http://im.yahooapis.jp/V201809">
      <ns2:license>1111-1111-1111-1111</ns2:license>
      <ns2:apiAccountId>2222-2222-2222-2222</ns2:apiAccountId>
      <ns2:apiAccountPassword>password</ns2:apiAccountPassword>
    </RequestHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <getUploadUrl xmlns="http://im.yahooapis.jp/V201809/Video">
      <accountId>1111</accountId>
      <uploadVideo>
        <videoName>TestUploadName</videoName>
        <videoTitle>TestVideoTitle</videoTitle>
        <userStatus>ACTIVE</userStatus>
      </uploadVideo>
    </getUploadUrl>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### レスポンス
| フィールド | データ型 | 説明 |
|---|---|---|
| rval | [UploadUrlPage](../data/Video/UploadUrlPage.md) | getUploadUrlメソッドの操作結果（全Entityのリスト）を表示します。|

##### ＜レスポンスサンプル＞
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header>
    <ResponseHeader xmlns="http://im.yahooapis.jp/V201809/Video" xmlns:ns2="http://im.yahooapis.jp/V201809">
      <ns2:service>Video</ns2:service>
      <ns2:requestTime>1536568330403</ns2:requestTime>
      <ns2:timeTakenSeconds>0.2671</ns2:timeTakenSeconds>
    </ResponseHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <ns2:getUploadUrlResponse xmlns="http://im.yahooapis.jp/V201809" xmlns:ns2="http://im.yahooapis.jp/V201809/Video">
      <ns2:rval>
        <totalNumEntries>1</totalNumEntries>
        <Page.Type>VideoPage</Page.Type>
        <ns2:values>
          <operationSucceeded>true</operationSucceeded>
          <ns2:uploadUrlValue>
            <ns2:accountId>1111</ns2:accountId>
            <ns2:acceptableUploadStatus>true</ns2:acceptableUploadStatus>
            <ns2:uploadUrl>https://colo01.im.yahooapis.jp/video/V201809/upload/Jzaaaebm9xhmuP5vZGnXkIHZ3FS8whNxwxiLMUjiqL4NLEc9gPf1uM58Ges40r0.chBFiNyw.z2I5Huw2TajPnlwRMIOo23Kv.oZGk1PTECEVSB_NNdoVhDDdImQKpsdbuG9rATPU5pPHyllotOhtkg8eEqlw--</ns2:uploadUrl>
          </ns2:uploadUrlValue>
        </ns2:values>
      </ns2:rval>
    </ns2:getUploadUrlResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## upload

### リクエスト
getUploadUrlで戻されたURLに対して、動画ファイルのアップロード処理を実施します。


### レスポンス


## mutate(SET)

### リクエスト
入稿済の動画の情報（動画名、配信状況）を変更します。

| パラメータ | 必須 | データ型 | 説明 |
|---|---|---|---|
| operations | ○ | [VideoOperation](../data/Video/VideoOperation.md) | 動画の情報を操作（変更）します。 |

##### ＜リクエストサンプル＞
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header>
    <RequestHeader xmlns="http://im.yahooapis.jp/V201809/Video" xmlns:ns2="http://im.yahooapis.jp/V201809">
      <ns2:license>1111-1111-1111-1111</ns2:license>
      <ns2:apiAccountId>2222-2222-2222-2222</ns2:apiAccountId>
      <ns2:apiAccountPassword>password</ns2:apiAccountPassword>
    </RequestHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <mutate xmlns="http://im.yahooapis.jp/V201809/Video">
      <operations>
        <operator>SET</operator>
        <accountId>11111</accountId>
        <operand>
          <accountId>1111</accountId>
          <mediaId>2222</mediaId>
          <videoTitle>Change Title</videoTitle>
          <userStatus>ACTIVE</userStatus>
        </operand>
      </operations>
    </mutate>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### レスポンス
| フィールド | データ型 | 説明 |
|---|---|---|
| rval | [VideoReturnValue](../data/Video/VideoReturnValue.md) | mutateメソッドの操作結果を表示します。 |

##### ＜レスポンスサンプル＞
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header>
    <ResponseHeader xmlns="http://im.yahooapis.jp/V201809/Video" xmlns:ns2="http://im.yahooapis.jp/V201809">
      <ns2:service>Video</ns2:service>
      <ns2:requestTime>1536568330429</ns2:requestTime>
      <ns2:timeTakenSeconds>0.2671</ns2:timeTakenSeconds>
    </ResponseHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <ns2:mutateResponse xmlns="http://im.yahooapis.jp/V201809" xmlns:ns2="http://im.yahooapis.jp/V201809/Video">
      <ns2:rval>
        <ListReturnValue.Type>VideoReturnValue</ListReturnValue.Type>
        <Operation.Type>SET</Operation.Type>
        <ns2:values>
          <operationSucceeded>true</operationSucceeded>
          <ns2:video>
            <ns2:accountId>1111</ns2:accountId>
            <ns2:mediaId>2222</ns2:mediaId>
            <ns2:videoName>tes</ns2:videoName>
            <ns2:videoTitle>tes2</ns2:videoTitle>
            <ns2:userStatus>ACTIVE</ns2:userStatus>
            <ns2:creationTime>20171024175716</ns2:creationTime>
            <ns2:approvalStatus>REVIEW</ns2:approvalStatus>
            <ns2:processStatus>FINISHED</ns2:processStatus>
            <ns2:videoSetting>
              <ns2:videoFileType>MP4</ns2:videoFileType>
              <ns2:videoAdFormat>YJ_640_360</ns2:videoAdFormat>
              <ns2:fileSize>29672732</ns2:fileSize>
              <ns2:width>640</ns2:width>
              <ns2:height>360</ns2:height>
              <ns2:playbackTime>60</ns2:playbackTime>
              <ns2:downloadOriginalUrl>https://colo01.im.yahooapis.jp/video/V201809/download/viZdXh.JqONCS1dU.dwWmnpIy_ITbPW2ahEb6ze_pZ4FID.XPbYHQc4zOEioYE7jhuJbrwX5QIcVv9H0cqQVszlNOzOY9aTuS1XYe7GUZhSasUj0tl2s1TWgbgxWmB004XRVt9FizVW_HXQgyYwgRjYJPQPqw4lcvbF1Vcf_UE8uLwhWwfbGjkkwwNIzbsDdLIceGTFbx7IiowQ9a73hWWArnvCbFWmBD.FN7HYd2FTGLoXKzcYZSDbMRMIs7HPkn4UvKqi_xLqKg_.33Ri0BmwfqhCnB7W2poxqddU8l15tMltkShxGURZ7zcdB.fwL1Q1KBmiltHhl6.0094X_HM.VLZjKAIhs4qiKLt9NMkpvL0bCygZHETuWkoIQZsg-</ns2:downloadOriginalUrl>
              <ns2:downloadHighBitrateUrl>https://colo01.im.yahooapis.jp/video/V201809/download/rwEr8wyJqOOhXYR9yKYWF3oViR5FAeebem9bEE72WgNqkhrVY4Bwfv6_1Yb6FrxOJcb9yXskjrcRwCEqHzqxOG_.8J4quw37bE0rleZHzh84Q1bAGwKUck3p70sWjOPopu1rcOJurCoo3.jhaHZVRQOGNFO7_HPJAeHEyN19IKjbBnIYFkZMatpHWTr20scfbJDt6AD0sE658RHSoNRSSj7XKxcawCw4seE9wsEQgGNwpNM2Y_ARzu3qURQOXya0J3LInGw0Cy_Jrg.ibPsf20ITAOhwX6tl8OyhcbSI1tHjUVIFxupeOImlJxtq8lDlYCPnleIHfGcNmrGXb7Our2rpT4POwzMXlc3YF4MrSI4XySxZpys3ZJe6Q6QEDFpz_Q--</ns2:downloadHighBitrateUrl>
              <ns2:downloadMiddleBitrateUrl>https://colo01.im.yahooapis.jp/video/V201809/download/vQRhca.JqOOhBifcqXbbRZlJOt1X9.v_2rNkYgSO71R03bXBDyBU5QoEm.O83ugEK9KTvFtFs6KU9bxBhqBwD8yzbNcP2euqi7wIkEfNY3OaQmYIVYFBi0dWq6aVUJwZPLepILE0vEJbNBpEuYCAq1r2Lk.wsG_QRgXZ3JTmuay58jYSjhc.v67VSBGvIHEZqYwdlr34Fuh7JwmBk0onAKVJL4bbghxXYlJH4x6C7Z9gBMlUkaVAEg9NEjoBwHOWbRLxC9SZ6acAc1Jv8z71OJ2dLu.NTIj2VPeGK35e4ogX8qI_HRFIjfZW_tT3Z3u..BpWQ6f0vc.NS1paxaoMU0BX8Dq.qIUFtRhuHEs9N0R3lQeswgbfQGz_qtr5</ns2:downloadMiddleBitrateUrl>
              <ns2:downloadLowBitrateUrl>video/V201809/download/vk88mJeJqON_XBRyO53kY9OWNrTQzPGAPZV2tklh5eqPV2nmecFPiOUoVl50VmnLSf8a2vCCp6TRX1iRRfFbfn8zQcYHwPu.clnL.ZFa1goVi9HnaNW9gi14xHfGUJV3WjRkhza8eBmL0_1.sN4P0odwRV2oRQCfGhuFL9jUK5oPNfNlmYV3F2gNEvDD.Lps8pDIuqIKSGVqH7.0kXrR.bU0Stvp_rkYBXTRLjDgi6YGgL96H0dlCF5aHEDnM.f6vKIq0qFxwRAWAWcz166YhTO8jYV9._QF_5z1e0nzMpeuQVZCXTf5UAU8eZDqhMXIvs7ztUfd1L5_6YJeTBm2Z34lF.m1WGrTlFmBHBFco5_2USOWKoz2cE4gGtVOA5c-</ns2:downloadLowBitrateUrl>
            </ns2:videoSetting>
          </ns2:video>
        </ns2:values>
      </ns2:rval>
    </ns2:mutateResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

## mutate(REMOVE)

### リクエスト
入稿済みの動画を削除します。

| パラメータ | 必須 | データ型 | 説明 |
|---|---|---|---|
| operations | ○ | [VideoOperation](../data/Video/VideoOperation.md) | 動画を操作（削除）します。 |

##### ＜リクエストサンプル＞
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header>
    <RequestHeader xmlns="http://im.yahooapis.jp/V201809/Video" xmlns:ns2="http://im.yahooapis.jp/V201809">
      <ns2:license>1111-1111-1111-1111</ns2:license>
      <ns2:apiAccountId>2222-2222-2222-2222</ns2:apiAccountId>
      <ns2:apiAccountPassword>password</ns2:apiAccountPassword>
    </RequestHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <mutate xmlns="http://im.yahooapis.jp/V201809/Video">
      <operations>
        <operator>REMOVE</operator>
        <accountId>11111</accountId>
        <operand>
          <accountId>1111</accountId>
          <mediaId>2222</mediaId>
        </operand>
      </operations>
    </mutate>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### レスポンス
| フィールド | データ型 | 説明 |
|---|---|---|
| rval | [VideoReturnValue](../data/Video/VideoReturnValue.md) | mutateメソッドの操作結果を表示します。 |

##### ＜レスポンスサンプル＞
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header>
    <ResponseHeader xmlns="http://im.yahooapis.jp/V201809/Video" xmlns:ns2="http://im.yahooapis.jp/V201809">
      <ns2:service>Video</ns2:service>
      <ns2:requestTime>1536568330463</ns2:requestTime>
      <ns2:timeTakenSeconds>0.2671</ns2:timeTakenSeconds>
    </ResponseHeader>
  </SOAP-ENV:Header>
  <SOAP-ENV:Body>
    <ns2:mutateResponse xmlns="http://im.yahooapis.jp/V201809" xmlns:ns2="http://im.yahooapis.jp/V201809/Video">
      <ns2:rval>
        <ListReturnValue.Type>VideoReturnValue</ListReturnValue.Type>
        <Operation.Type>SET</Operation.Type>
        <ns2:values>
          <operationSucceeded>true</operationSucceeded>
          <ns2:video>
            <ns2:accountId>1111</ns2:accountId>
            <ns2:mediaId>2222</ns2:mediaId>
            <ns2:videoName>tes</ns2:videoName>
            <ns2:videoTitle>tes2</ns2:videoTitle>
            <ns2:userStatus>ACTIVE</ns2:userStatus>
            <ns2:creationTime>20171024175716</ns2:creationTime>
            <ns2:approvalStatus>REVIEW</ns2:approvalStatus>
            <ns2:processStatus>FINISHED</ns2:processStatus>
            <ns2:videoSetting>
              <ns2:videoFileType>MP4</ns2:videoFileType>
              <ns2:videoAdFormat>YJ_640_360</ns2:videoAdFormat>
              <ns2:fileSize>29672732</ns2:fileSize>
              <ns2:width>640</ns2:width>
              <ns2:height>360</ns2:height>
              <ns2:playbackTime>60</ns2:playbackTime>
              <ns2:downloadOriginalUrl>https://colo01.im.yahooapis.jp/video/V201809/download/viZdXh.JqONCS1dU.dwWmnpIy_ITbPW2ahEb6ze_pZ4FID.XPbYHQc4zOEioYE7jhuJbrwX5QIcVv9H0cqQVszlNOzOY9aTuS1XYe7GUZhSasUj0tl2s1TWgbgxWmB004XRVt9FizVW_HXQgyYwgRjYJPQPqw4lcvbF1Vcf_UE8uLwhWwfbGjkkwwNIzbsDdLIceGTFbx7IiowQ9a73hWWArnvCbFWmBD.FN7HYd2FTGLoXKzcYZSDbMRMIs7HPkn4UvKqi_xLqKg_.33Ri0BmwfqhCnB7W2poxqddU8l15tMltkShxGURZ7zcdB.fwL1Q1KBmiltHhl6.0094X_HM.VLZjKAIhs4qiKLt9NMkpvL0bCygZHETuWkoIQZsg-</ns2:downloadOriginalUrl>
              <ns2:downloadHighBitrateUrl>https://colo01.im.yahooapis.jp/video/V201809/download/rwEr8wyJqOOhXYR9yKYWF3oViR5FAeebem9bEE72WgNqkhrVY4Bwfv6_1Yb6FrxOJcb9yXskjrcRwCEqHzqxOG_.8J4quw37bE0rleZHzh84Q1bAGwKUck3p70sWjOPopu1rcOJurCoo3.jhaHZVRQOGNFO7_HPJAeHEyN19IKjbBnIYFkZMatpHWTr20scfbJDt6AD0sE658RHSoNRSSj7XKxcawCw4seE9wsEQgGNwpNM2Y_ARzu3qURQOXya0J3LInGw0Cy_Jrg.ibPsf20ITAOhwX6tl8OyhcbSI1tHjUVIFxupeOImlJxtq8lDlYCPnleIHfGcNmrGXb7Our2rpT4POwzMXlc3YF4MrSI4XySxZpys3ZJe6Q6QEDFpz_Q--</ns2:downloadHighBitrateUrl>
              <ns2:downloadMiddleBitrateUrl>https://colo01.im.yahooapis.jp/video/V201809/download/vQRhca.JqOOhBifcqXbbRZlJOt1X9.v_2rNkYgSO71R03bXBDyBU5QoEm.O83ugEK9KTvFtFs6KU9bxBhqBwD8yzbNcP2euqi7wIkEfNY3OaQmYIVYFBi0dWq6aVUJwZPLepILE0vEJbNBpEuYCAq1r2Lk.wsG_QRgXZ3JTmuay58jYSjhc.v67VSBGvIHEZqYwdlr34Fuh7JwmBk0onAKVJL4bbghxXYlJH4x6C7Z9gBMlUkaVAEg9NEjoBwHOWbRLxC9SZ6acAc1Jv8z71OJ2dLu.NTIj2VPeGK35e4ogX8qI_HRFIjfZW_tT3Z3u..BpWQ6f0vc.NS1paxaoMU0BX8Dq.qIUFtRhuHEs9N0R3lQeswgbfQGz_qtr5</ns2:downloadMiddleBitrateUrl>
              <ns2:downloadLowBitrateUrl>video/V201809/download/vk88mJeJqON_XBRyO53kY9OWNrTQzPGAPZV2tklh5eqPV2nmecFPiOUoVl50VmnLSf8a2vCCp6TRX1iRRfFbfn8zQcYHwPu.clnL.ZFa1goVi9HnaNW9gi14xHfGUJV3WjRkhza8eBmL0_1.sN4P0odwRV2oRQCfGhuFL9jUK5oPNfNlmYV3F2gNEvDD.Lps8pDIuqIKSGVqH7.0kXrR.bU0Stvp_rkYBXTRLjDgi6YGgL96H0dlCF5aHEDnM.f6vKIq0qFxwRAWAWcz166YhTO8jYV9._QF_5z1e0nzMpeuQVZCXTf5UAU8eZDqhMXIvs7ztUfd1L5_6YJeTBm2Z34lF.m1WGrTlFmBHBFco5_2USOWKoz2cE4gGtVOA5c-</ns2:downloadLowBitrateUrl>
            </ns2:videoSetting>
          </ns2:video>
        </ns2:values>
      </ns2:rval>
    </ns2:mutateResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

<a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/"><img alt="クリエイティブ・コモンズ・ライセンス" style="border-width:0" src="https://i.creativecommons.org/l/by-nd/2.1/jp/88x31.png" /></a><br />この 作品 は <a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/">クリエイティブ・コモンズ 表示 - 改変禁止 2.1 日本 ライセンスの下に提供されています。</a>
