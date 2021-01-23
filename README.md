# superset
superset + apache drill

# 使い方
1.Supersetの開始<br>
`
docker-compose up -d
`

2.supersetの初期化＆adminユーザー作成<br>
(コマンド後の案内が出てくるのでそれに従って設定)<br>
`
docker-compose -it superset 
`

3.画面に移動<br>
` http://localhost:8088 `
にアクセスして下さい

4.その他<br>
今回のサンプルはDBにテストデータ入れるが面倒だったためローカルにjsonファイルを配置して、それをクエリーするようにしています。
(その際にapache drill( https://drill.apache.org/ )というエンジンを使っています。)
以下apache drillをsuperset内で使う際の手順です。

4-1.datasourceへの接続URL<br>
drillを使う際のSQLAlchemy URLは
`
drill+sadrill://drill:8047/dfs?use_ssl=False
`
を設定して下さい。

4-2.drillからローカルファイルに対してのクエリー<br>
サンプルSQL<br>
``
SELECT *
FROM dfs.`/Data/sample.json`
``
