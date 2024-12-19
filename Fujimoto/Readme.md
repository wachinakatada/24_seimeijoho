
講義名：琉球大学農学部『生命情報科学』　解析環境整備  
作成日：2024/12/19  
作成者：藤本真悟（総合技術部)   

### 1. 実施にあたって

生命情報科学では、様々な解析ソフトや公共データベースを参照して計算機で処理を実行します。
本講義は、そうした処理を実行する解析環境として、琉球大学・研究基盤統括センターに設置された
計算機サーバーにリモート接続して、計算してみるワークショップ形式で進めます。  
  
ソフトウェアのインストールとサーバーへの接続に必要なネットワーク設定の詳細を、
琉球大学ウェブクラスの生命情報科学の項目内にアップロードしました。
「解析環境整備（担当：藤本）」の項目から、PDF資料をダウンロードして準備してください。  
https://webclass.cc.u-ryukyu.ac.jp/webclass/login.php
  
&nbsp;
&nbsp;
&nbsp;
&nbsp;
  

### 2. ファイル転送とリモート接続ツールの紹介   
### (Mac, Linux の場合, Windowsは後述する"3"を参照)  

**Filezilla: https://filezilla-project.org/**  
個人のPCと計算機サーバー間で、ファイルのアップロード/ダウンロードを
実行するためのソフトウェアです。

**Terminal:**  
MacやLinuxでは、デフォルトでインストールされたコマンドライン操作のツールを使用して、
計算機サーバーと接続して操作します。検索窓に「Terminal」と入力すると実行画面が表示されます。  
Dockに追加しておくと便利かもしれません。
  
&nbsp;
&nbsp;
&nbsp;
&nbsp;
  
### 3. ファイル転送とリモート接続ツールの紹介 (Windowsの場合)  

**Filezilla: https://filezilla-project.org/**  
(Mac, Linuxの項目で紹介しているのと同じソフトウェアの Windows 版)

**Putty: https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html**  
他のコンピュータにリモート接続するためのクライアントソフト。
  
&nbsp;
&nbsp;
&nbsp;
&nbsp;
  
### 4. UNIXコマンドの実行と共有フォルダの確認
[xxxxx@server.address ~]$ ls /mnt/bioInfo2024_share
  
&nbsp;
&nbsp;
&nbsp;
  
