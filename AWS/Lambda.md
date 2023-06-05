## Amazon Lambda

サーバーなどのコンピューティングリソースを意識することなく、<b>Lambda関数</b>と呼ばれるアプリケーションコードをデプロイしただけで実行することができるサーバーレスなサービス。

### ExecutionRole

LambdaにアタッチされたIAMロールのこと。

Lambdaは、IAMロールの権限に従って書くAWSサービスへアクセスするため、IAMロールによるアクセス制御設計が必要となる。そこでこのExecutionRoleを利用する。

### ロギング

すべてのLambda関数の処理結果はCloudWatch Logsに保存される。

### Lambda@Edge

Lambdaという名前がついているが、実際には、CloudFrontの機能。



