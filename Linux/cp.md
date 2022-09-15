## cp

ファイルやディレクトリのコピーを作成する際に使用する。

`cp コピー元　　　コピー先`

```
// 現在のファイルの状況をtreeで確認。sampleはディレクトリ。
tree
.
├── hito.rtf
├── hito2.txt
├── hito3.txt
├── hito4.txt
└── sample

1 directory, 4 files
```

```
//hito4.txtに対してsampleディレクトリ内へコピーを作成
cp hito4.txt sample
tree
.
├── hito.rtf
├── hito2.txt
├── hito3.txt
├── hito4.txt
└── sample
    └── hito4.txt

1 directory, 5 files
```

コピー先の名称を変更しつつ、コピーを作成することもできる。hito3.txtをuma3.txtに変更しつつ、sampleディレクトリへコピーを作る。

```
cp hito3.txt sample/uma3.txt
tree
.
├── hito.rtf
├── hito2.txt
├── hito3.txt
├── hito4.txt
└── sample
    ├── hito4.txt
    └── uma3.txt

1 directory, 6 files
```

-pオプションをつけることで、コピー元のパーミッション（閲覧権限や実行権限）の設定を引き継げるので、基本的に-pオプションは付けるようにする。







