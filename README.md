Session: https://camo.githubusercontent.com/10cd8f8251ec9d1acf0d6c7e26d69415575c0f94b27c26c99c893e1743d6f4a2/68747470733a2f2f63646e2e61757468302e636f6d2f626c6f672f636f6f6b6965732d76732d746f6b656e732f636f6f6b69652d746f6b656e2d617574682e706e67

arsitektur:
- monolitich
  Yii, Laravel, CI, Wordpress
  MVC=>
    - Model => database
    - View  => tampilan ke user
    - Controller => routing (calo antara model sama view)
  kelebihan:
    - g banyak yang di maintenance
    - lebih simple
  kekurangan:
    - Berat
    - jika down 1 module maka module lain down juga
    
    dwi  => login 1X=> transaksi 10X
                       transaksi ke-1
                       .....
                       transaksi ke-10
                       xxxxxxx
    will => login 1X=> transaksi 50X
                       transaksi ke-1
                       .....
                       transaksi ke-40
                       xxxxxxx
                       transaksi ke-50
    eko => login X => 
    
    
    User=>Aplikasi=>Database
  
- multi tier / N tier
  BackEnd  => berhubungan sama database (model) dengan output JSON (DOM)
    - Contoh: Nodejs, php (lumen, yii minimal), golang, java, python, C
====================================================================================
  FrontEnd => view / yg berhubungan dengan user dan mengolah JSON (DOM) dari BackEnd
    - Contoh: NodeJS (vue, react, angular)
  User => FrontEnd => BackEnd => Database
  
- microservice
  jenis: share database, api gateway, message broker(streaming data)
  FrontEnd
    => NodeJS, Kotlin
  BackEnd
    => PHP, python, NodeJS
    => database: (user, barang, transaksi, report, OTP)
    => service user(golang), service OTP(java), service barang(php), service transaksi(php), service report (python), leader/api gateway(golang)
    
    
    
    ENDPOINT

HTTP request: GET, POST, PUT, DELETE, PATCH, HEAD
HTTP respon: 200(sukses), 400(permission deny), 404(page not found), 500(internal server error)
    
- bikin dokumentasi : swagger UI
- bikin versi : 
    - versi 1 (https://developer.tokopedia.com/openapi/guide/#/product/getallvariant?id=get-all-variants-by-category-id)
    - versi 2 (https://developer.tokopedia.com/openapi/guide/#/product/getallvariant?id=get-all-variants-by-category-id-v2)
- pilih framework paling ringan : lumen
- bikin pattern : /module, /module/id
    /v1/module => GET (select * FROM)
                  {data: {id: xxxx, name:xxxxx, date_at: xxxxxx}}
               => POST (insert into)
    /v1/module/id => GET (select * FROM WHERE id)
                  => POST/PUT (update set)
                  => DELETE (delete from)
    