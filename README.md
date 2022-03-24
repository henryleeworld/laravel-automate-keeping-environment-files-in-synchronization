# Laravel 9 自動保持環境檔案同步

引入 worksome 的 envy 套件來擴增自動保持環境檔案同步，您有多少次將新開發人員加入您的團隊，卻因為您專案的 .env.example 檔案已經過時而不得不花費很長時間與他們一起除錯？如果您和我們一樣的話，數不勝數。如果有辦法確保您的環境檔案保持最新，那不是很好嗎？

## 使用方式
- 把整個專案複製一份到你的電腦裡，這裡指的「內容」不是只有檔案，而是指所有整個專案的歷史紀錄、分支、標籤等內容都會複製一份下來。
```sh
$ git clone
```
- 將 __.env.example__ 檔案重新命名成 __.env__，如果應用程式金鑰沒有被設定的話，你的使用者 sessions 和其他加密的資料都是不安全的！
- 當你的專案中已經有 composer.lock，可以直接執行指令以讓 Composer 安裝 composer.lock 中指定的套件及版本。
```sh
$ composer install
```
- 產生 Laravel 要使用的一組 32 字元長度的隨機字串 APP_KEY 並存在 .env 內。
```sh
$ php artisan key:generate
```
- 執行 __envy:sync__ 指令來搜尋專案的設定檔中的環境設定，將它們與您配置的環境檔案（預設情況下只是您的 .env.example）進行比較，以尋找遺漏的變數。
```sh
$ php artisan envy:sync
```
- 執行 __envy:prune__ 指令來搜索專案的設定檔中的環境設定（預設情況下只是您的 .env.example），以尋找在任何設定檔中都找不到的變數。
```sh
$ php artisan envy:prune
```

----

## 畫面截圖
![](https://i.imgur.com/UGCs5TT.png)
> 可以將環境檔案與設定檔保持同步
