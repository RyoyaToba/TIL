## mv

ファイルやディレクトリを移動させるときに使用する。cpコマンドとの違いはファイルの移動元からはファイルがなくなる。

`mv 移動元　移動先`

```
tree
.
├── hito.rtf
├── hito2.txt
├── hito3.txt
└── sample
    ├── hito4.txt
    └── uma3.txt
```

hito3.txtをsampleディレクトリ下に移動させる

```
mv hito3.txt sample
tree
.
├── hito.rtf
├── hito2.txt
└── sample
    ├── hito3.txt
    ├── hito4.txt
    └── uma3.txt
```

cpと同様に、名前を変更しながら移動することも可能

hito2.txtをuma2.txtに変更しつつ、sample下に移動する

```
mv hito2.txt sample/uma2.txt
tree
.
├── hito.rtf
└── sample
    ├── hito3.txt
    ├── hito4.txt
    ├── uma2.txt
    └── uma3.txt
```

名称の変更だけなら、おそらく

```
mv hito.rtf uma.rtf
tree
.
├── sample
│   ├── hito3.txt
│   ├── hito4.txt
│   ├── uma2.txt
│   └── uma3.txt
└── uma.rtf
```

できました。tree表示の順番は変わるんですね。
