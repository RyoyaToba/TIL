## EC2

AWSクラウド上の仮想サーバーを提供する、AWSの代表的なコンピューティングサービス。

このサービスを利用して作成された仮想サーバーのことを<b>EC2インスタンス</b>という。

ユーザーはAWSマネジメントコンソール上で行う簡単な操作で、必要な台数、必要なスペックのEC2インスタンスを容易に構築できる。スペックは容易に変更可能。従量課金制度なので、利用した
分だけのコストを負担するだけで済む。

<br>

### EC2インスタンス作成の流れ

1. Amazon Machine Image(AMI)の選択
2. インスタンスタイプの選択
3. インスタンスの詳細設定
4. ストレージの設定
5. タグの追加
6. セキュリティグループの設定
7. キーペアの設定

<br>

### Amazon Machine Image(AMI)

EC2インスタンスを作成する際に使用する仮想マシーンイメージで、EBSのスナップショットとEC2インスタンスの構成情報から構成されている。

OSには、Red Hat Enterprise Linuxや、Ubuntuなどの各種Linuxディストリビュージョンと、Microsoft Windows Serverの他、AWSが提供しているAmazon Linuxが利用可能。

AMIをAuto Scallingなどのサービスで指定することで、同じ設定のEC2インスタンスを、必要な時に必要な分だけ自動で構築することができる。

AMIは、<b>EBS-Backend</b>もしくは<b>Instance Store-Backend</b>のどちらかに分類される。

<br>

#### EBS-Backend

EBSをOSのルート領域として利用したEC2インスタンス。

#### Instance Store-Backend

インスタンスストアをOSのルート領域として利用したEC2インスタンス。





