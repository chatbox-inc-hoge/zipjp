## 日本語 ZIP CODE 関連ライブラリ

ZIP CODE 系マスターDBの生成サンプル
各種 Yamlの吐き出し(Yaml化してしまえばDBに突っ込める?)

APIサーバ

日本郵便提供のCSVは結構大きい
DBなしでの運用を考えるなら、CSVの分割は必須。
(基本的に縦断検索は無いだろうから問題ない?)

提供CSVの都道府県別分割。

郵便番号規則は結構グチャグチャなので機械的に振り分けするのは結構難しいかも。

heroku運用したいです。

vue.js使ってモーダル型プラグイン。

## API

全てGET。認証なし

### /zip/xxxxxxx

ZIPコードからデータを返す。

->  
status: "OK"
address: Address

### /pref

都道府県一覧を返す。

->
status: "OK"
address: PrefAddress



### /address/{pref}

都道府県名から所属地域の郵便番号一覧を返す。

->
status: "OK"
address: Address[]

### API 応答型
Adress
	zipcode   7桁郵便番号
	zipcode3  上3桁郵便番号
	zipcode4  下4桁郵便番号
	pref
	city
	prefKana
	cityKana
	prefRoma
	cityRoma

PrefAddress
	zipcode   代表郵便番号
	zipcodes  郵便番号範囲
	pref
	prefKana
	prefRoma

