## AWS

使い方メモ

**sshによるEC２への接続**

ssh -i 「keyのパス」 「ユーザー名」@「IPアドレス」

ssh -i ~/Desktop/aws-and-infra-ssh-key.pem ec2-user@〜〜〜

**Apacheの起動確認**

sudo systemctl status httpd.service

**Apacheの再起動**

sudo systemctl restart httpd.service

**mysqlへの接続**

mysql -h 「EndPoint」 -u root -p
