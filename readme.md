---
title: 股神(策略通)
tags: 相關環境
---

## 整理/重構 PART 2
* Warning看能不能修掉 
  * CSS styleName can't resolve ==Webpack設定問題==
  * Webpack multiple files export to the same file ==Webpack設定問題==
  * 專案開啟後,開發者工具有看到一些有的沒的error (並不影響使用者)
* 照ESLint建議改寫=>像是無狀態的class改寫成function(效能會比較好), prefer destructuring, import cycle...等等族繁不及備載
  * 檢查現在所有ESLint disable的地方,是否為"必須修復不宜忽略" 
  * ESLint的error+warning蠻多的, 有1000+條
  * 曾把某class改寫成React的class, state卻出錯
  * 若看過覺得某error/warning不重要,會修改ESLint規則
  * 現在專案用的是airbnb這個規則,其實是最最嚴謹的規則,所以專案一片紅,很正常 (接手時,原本專案就用這個規則了,但看起來以往開發人員開發時,並沒有開啟ESLint,所以並沒有遵循規則在開發)
* React 16.8推出Hook,生命週期官方有調整過
  * 目前專案內有蠻多,16.8過後官方建議不要使用的生命週期,目前已改為官方建議的暫時寫法==UNSAFE_componentWillReceiveProps()==, ==UNSAFE_componentWillMount()==, 可考慮是否改寫成16.8之後的做法==useEffect==
* 專案內的innerHTML,可能牽扯到安全性問題
  * 確定innerHTML,不會被放入JavaScript
* nodemon/webpack/babel移除,改用CRA => ==目前困難點如下==
  * CRA要求所有檔案放在src下面,跟現在的專案結構不同,images必須放在public裡面或者src/assets裡面,且似乎有層數限制!!!!!!
  * ~~Webpack設定複雜(尤其H5),改寫不太容易~~(尚可解決) 
  * ~~專案內有用到Babel的decorator及其他套件,即使換到CRA也要加裝其他plugin去overwrite CRA預設的Babel設定~~(尚可解決) 

## 網域
:::info
192.168為各自辦公室

10.*為香港公司內部ip
:::

## 週報
[Dropbox](https://www.dropbox.com/home/weekly_report)

## 週報格式
週報請依下列格式，每週二中午前發在skype開發群組

==[分類] 工作項目：現況描述==

NOTE: [分類] 可以是 [完成] [進行] [待辦]

## 工作管理工具
[禪道](zentao.coltech.hk/zentao/user-login-L3plbnRhby8=.html)
**用戶名:** ==alice==
**密碼:** ==Aa123456==

## Google帳號
**用戶名:** ==sincereitsl.it3@gmail.com==
**密碼:** ==SincereIT2021==


## 測試環境(香港)
### 两融策略管理平台
http://10.0.2.201:8089/wpmanager/index.html#
**用戶名:** ==admin==
**密碼:** ==123456==

### 測試机的H5
http://10.0.2.203/#/home 
**用戶名:** ==13900000000== 
**密碼:** ==123456==

### 另一個環境(對外)的H5
http://clt.coltechhk.cn/
**用戶名:** ==17777777777== 
**密碼:** ==111111==

### 測試机的PC-WEB
http://10.0.2.201:8111/#/home
**用戶名:** ==13900000000== 
**密碼:** ==123456==

#### 對應的資料庫
**host:** ==10.0.2.201==
**port:** ==3306==
**username:** ==root==
**password:** ==p12345==

## TeamViewer
alice1qaz@gmail.com
1q2w3e4R
号 166669042


## Git資訊
[Git](https://103.68.61.92:8443/)
**用戶名:** ==alice==
**密碼:** ==alice!@#0609==


:::warning
* 如果clone不下來,要調整http.sslVerify 

  * For a single repo

    `git config http.sslVerify false`

  * For all repo

    `git config --global http.sslVerify false`

* ~~npm公用庫的server沒了,只能手動拉到node_modules,所以package.json跟實際node_modules裡面有的內容,絕對不一樣~~(重構已解決)
* ~~node版本請使用10.17.0~~(重構已解決)
* 跑npm start, SCSS的warning不會影響運行
* 如果dev分支上的config.js,跑npm start跑不起來,可以拿測試環境的config.js複製貼上
  ![](https://i.imgur.com/75hGmNt.png)
* 一律在dev分支開發,master已荒廢
* 如果有新的統一標準eunis那邊會跟大家說,目前只要git上有對應版本號的識認就ok
:::


[运维SVN](https://103.68.61.93/svn/2项目管理/1大中华软件/1策略通系统)
* ==https://103.68.61.93/svn/2项目管理/1大中华软件/1策略通系统==
* .93,support部的,是把==測試完成==的包,放上去的
* 用户名：alice
* 密码：alice!@#0609


[开发SVN](https://103.68.61.92/svn/ProjectManagement/3.1产品项目/)
* ==https://103.68.61.92/svn/ProjectManagement/3.1产品项目/3.1.10 策略通/3.1.1.3 开发提测==
* .92,開發部的,是用來把==開發完==的代碼打了包后發上去的
* 用户名：alice
* 密码：alice!@#0609

==SVN要下載tortoiseSVN==

## Git tag
[說明](https://git-scm.com/book/en/v2/Git-Basics-Tagging)

![](https://i.imgur.com/1iQhubX.png)


## 開發流程
* 開發的环境，是你自己操作的本机，一般是你自己本机開發完成后
* 打包，交由香港Java佈署到測試机，然后測試有沒有問題，有問題再debug，沒有問題后
* 發布到git，然后打包放到svn
  * 把新版的binary照公司規定壓縮（成.zip)及命名，在svn repository上建立新目錄，放置此壓縮檔
  * svn是上一代的板控系統，TortoiseSVN是整合Windows檔案總管的svn圖形界面，很好用，還有TortoiseGIT對應到git
* 測試人員在另外的測試环境測試，如果沒有問題，就可以發布到客戶那边了

## svn打包範例

![](https://i.imgur.com/kW1ZlRl.png)

![](https://i.imgur.com/rxTYLe1.png)



* 發布v2.1.1的例子
* 用repo-browser以公司規定在遠端svn repo上建立新版本目錄
* checkout此目錄
* 壓縮檔放進去
* commit
* 完成

:::warning

提交新版本到 .92 .93 時
1. 先建立 ${版號}/${日期}/${程式語言} 目錄
2. 下面擺放 binary 壓縮檔 和 文字說明文件（說明新版差異）
:::


## 香港同事上班時間
* 9:00-12:00 13:00-17:30

## 現有開發人員
![](https://i.imgur.com/FsXBznX.png)


## NAS系統
NAS系統 : http://192.168.1.250:5000/
電腦共享區 :  ==\\\192.168.1.250==
帳號 : IT02
密碼 : F2zvz)OS

---

## Update history
==Newer on the top==
| Date       | Author | Description     |
|:---------- |:------:|:--------------- |
| 21/07/2021 | Alice  | modify content |
| 15/06/2021 | Alice  | modify content |
| 10/06/2021 | Alice  | add content |
| 09/06/2021 | Alice  | initial version |