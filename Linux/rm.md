## rm

ファイルの削除を行うことができる。

```
//　存在ファイルの確認
ls
hito.rtf	hito2.txt	hito3.txt	hito4.txt

// 削除を実行後、再度確認
rm hito3.txt
ls
hito.rtf	hito2.txt	hito4.txt
```

ディレクトリの削除も行うことができる。その際は-tオプションをつける。

```
// sampleディレクトリの作成
mkdir sample
ls
hito.rtf	hito2.txt	hito4.txt	sample

// -rなしではディレクトリの削除はできない
rm sample
rm: sample: is a directory

// rm -r sample
ls
hito.rtf	hito2.txt	hito4.txt
```
