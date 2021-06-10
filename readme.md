---
title: 相關環境
tags: 策略通
---

## 網域
:::info
192.168為各自辦公室
10.*為香港公司內部ip
:::


## 週報
[Dropbox](https://www.dropbox.com/home/weekly_report)

## 測試環境(香港)
### 两融策略管理平台
http://10.0.2.201:8080/wpmanager/index.html#
admin
123456

### H5
http://10.0.2.203/#/home
用戶名：13900000000
密碼：123456


## TeamViewer
alice1qaz@gmail.com
1q2w3e4R
号 166669042


## Git資訊
[Git](https://103.68.61.92:8443/)
用户名：alice
密码：alice!@#0609


[运维SVN](https://103.68.61.93/svn)
用户名：alice
密码：alice!@#0609


[开发SVN](https://103.68.61.92/svn)
用户名：alice
密码：alice!@#0609

==SVN要下載tortoiseSVN==


## 週報格式
週報請依下列格式，每週二中午前發在skype開發群組

==[分類] 工作項目：現況描述==

NOTE: [分類] 可以是 [完成] [進行] [待辦]


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
| 10/06/2021 | Alice  | add content |
| 09/06/2021 | Alice  | initial version |