# 概要
* Ubuntu（Debian）でのWebサーバー構築方法。
* 手順は2026年現在。

## コマンド
### ①：パッケージをアップデートする
* これをしないとパッケージが見つからないことがあります
```sudo apt-get update```

### ②：webサーバーに必要なものをインストール
```sudo apt-get install apache2 php ufw```

### ➂：Ubuntu側のポート開放を行う
* ポート開放をしないと、サーバーを起動しても、ウェブページにアクセスできません（ただし、ルーターなどでも開放を別途行う必要があります）。<br>
```sudo ufw enable``` - ポート開放するツールを有効にするコマンド <br>
```sudo ufw allow 80``` - ウェブページで使うポート（80番）を開放するコマンド <br>
```sudo ufw reload``` - ポート開放の情報を更新するコマンド <br>
#### 結果
sudo ufw status と打って、以下のように出れば問題ありません。
```
user@○○:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
80                         ALLOW       Anywhere
80 (v6)                    ALLOW       Anywhere (v6)
```

### ④：アクセスする
```localhost```　にアクセスし、以下のように表示されれば、成功です。
<img width="1597" height="922" alt="" src="https://github.com/user-attachments/assets/7f1cf104-fba1-45a3-8b1e-0a8695ef68f4" />

### ⑤：ファイルを変えるには
デフォルトでは、 /var/www/html/ にあります。そこにファイルを置くことで変更することができます。
```shell
user@○○:~$ cd /var/www/html/
user@○○:/var/www/html$ ls
index.html
```



