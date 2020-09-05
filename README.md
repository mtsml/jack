# Jack Project
## アプリ一覧

|名前|本番環境|リポジトリ|さくせん|
|--|--|--|--|
|Django Jack|[ここ](https://django-jack.herokuapp.com/)|[ここ](https://github.com/mtsml/django-jack)|ガンガンいこうぜ|
|Laravel Jack|[ここ](https://laravel-jack.herokuapp.com/)|[ここ](https://github.com/mtsml/laravel-jack)|バッチリがんばれ|
|View Jack|準備中…|[ここ](https://github.com/mtsml/view-jack)|いのちだいじに|
|Bash Jack|[ここ](http://hoge.hagetaka.art/index)|[ここ](https://github.com/mtsml/bash-jack)|フレームワークつかうな|
|Angular Jack|[ここ](https://angular-jack.herokuapp.com/)|[ここ](https://github.com/mtsml/angular-jack)|ガンガンいこうぜ|

## データ構造
### ER図
![ER図](./er.png)

### エンティティ一覧
#### channel
Youtubeのチャンネル情報を管理する。

「Youtube API」に日毎のリクエスト制限が存在するため、チャンネル名はアプリケーションで動的に取得せずに、属性として保持している。

|物理名|型|主キー|必須|説明|
|--|--|--|--|--|
|channel_id|varchar|1|Yes|チャンネルID|
|channel_nm|varchar||Yes|テーブル**追加時**のチャンネル名|

#### video
Youtubeの動画情報を管理する。

動画は必ずチャンネルに紐づく。

|物理名|型|主キー|必須|説明|
|--|--|--|--|--|
|video_id|varchar|1|Yes|動画ID|
|channel_id|varchar||Yes|動画が紐づくチャンネルID|

#### comment
アプリケーションで作成されたコメントを管理する。

コメントはチャンネルまたは動画に作成することができるため、外部キーを設定することができない（テーブル分けるべき？）

|物理名|型|主キー|必須|説明|
|--|--|--|--|--|
|category|varchar|1|Yes|コメントの種別 [```channel```, ```video```]|
|foreign_id|varchar|2|Yes|チャンネルIDまたは動画ID|
|comment|varchar||Yes|コメント|
|reg_datetime|datetime||Yes|コメント作成日時|