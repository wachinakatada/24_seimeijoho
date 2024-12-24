## コマンドライン入門
和智仲是（熱帯生物圏研究センター・西表研究施設）

2021年12月21日版; 2022年12月19日改訂; 2022年12月24日改訂(藤本);

## 1. 基本的なコマンド

### 1.1. cd（しーでぃ）

```sh
# ホームディレクトリに移動
$ cd

# 絶対パスで移動
$ cd /home
$ cd /home/bioUser[xx]
$ cd ../ # 一つ上のディレクトリ(/home)に移動

# 相対パスで移動
$ cd bioUser[xx] # /home ディレクトリにいれば、移動できる
```

### 1.2. pwd（ぴーだぶりゅでぃー）
```sh
# 現在のディレクトリ（カレントディレクトリ）を表示
$ pwd
# /home/bioUser[xx] と表示されるはず
```

### 1.3. mkdir（えむけいでぃあ）
```sh
# ディレクトリを作成
$ mkdir [ディレクトリ名]
```

### 1.4. ls（えるえす）
```sh
# カレントディレクトリのファイルやディレクトリを表示
$ ls

# ファイルとディレクトリを区別して表示
$ ls -F
```

### 1.5. touch
```sh
空のファイルを作成する
$ touch [ファイル名] 
```

### 1.6. mv（むーぶ）
**（元のファイルはなくなることに注意）**

```sh
# ファイルを移動
mv [ファイル名] [移動先ディレクトリ名]

# ファイル名の変更
mv [ファイル名] [新ファイル名]
```

### 1.7. cp（こぴー）
（文字通りコピーを作る）
```sh
# ファイルをコピーする
cp [ファイル名] [コピー先ディレクトリ名]

# ファイルの内容をコピーする
cp [ファイル名] [コピーファイル名]
```

### 1.8. rm（あーるえむ）
**（即座にファイルが消去されるので要注意）**

```sh
# ファイルを消去する
rm [ファイル名]
```



### 演習1: ここまでのコマンドを使ってみよう
```sh
# 適当なディレクトリを作成する
$ mkdir bioinfo

# 作成したディレクトリに移動する
$ cd bioinfo

# 空のファイル file1.txt を作成する
$ touch file1.txt

# file1.txt を file2.txt に移動（ファイル名の変更）
$ mv file1.txt file2.txt

# 確認
$ ls
file2.txt

# file2.txtを消去
rm file2.txt

# 空のファイル file3.csv を作成する
touch file3.csv

# file3.csv を file4.csv にコピーする
cp file3.csv file4.csv

# 確認
$ ls
file3.csv	file4.csv
```


### 発展1. ワイルドカード

```sh
# 適当なディレクトリを作成する
$ mkdir dir1

# 空ファイル file1.txt と file2.txt を作成する
touch file1.txt file2.txt

# 確認（-Fのオプションのある時とない時の違いに注意）
$ ls
dir1		file1.txt	file2.txt	file3.csv	file4.csv
$ ls -F
dir1/		file1.txt	file2.txt	file3.csv	file4.csv

# ワイルドカードを使って、当てはまるものだけディレクトリ dir1 に移動する
$ mv *.csv dir1/

# 確認
$ ls
dir1		file1.txt	file2.txt
$ ls dir1/
file3.csv	file4.csv
```



## 2. ファイルの中身をみる

### 2.1. less（れす）

**ページを閉じるには q を入力する**

```sh
# ファイルの中身を1ページずつ表示
$ less [ファイル名]
```

### 2.2. cat（きゃっと）

```sh
# ファイルの中身を全て表示する
$ cat [ファイル名]
```

### 2.3. grep（ぐれっぷ）

```sh
# 指定した文字列が含まれる行を出力する
$ grep [検索したい文字列] [検索対象のファイル名]
```

### 2.4. wc（だぶるしー）

```sh
# 行数・単語数・バイト数を出力する
$ wc [調べたいファイル名]

# 行数のみ出力する
$ wc -l [調べたいファイル名]
```



### 演習2. ここまでのコマンドを使ってみよう

ヒト・ボノボ・チンパンジー・ゴリラの腸内細菌を比較した研究 [Moeller, A. H., Caro-Quintero, A., Mjungu, D., Georgiev, A. V., Lonsdorf, E. V., Muller, M. N., ... & Ochman, H. (2016). Cospeciation of gut microbiota with hominids. *Science*, *353*(6297), 380-382.] のデータの一部を改変して利用

**ファイル転送ツールを使うとき**
`/mnt/bioInfo2024_share/wachi/data`をコピーする

**共有サーバー上で作業をするとき**
```sh
cp -r /mnt/bioInfo2024_share/wachi/data exe2
cd exe2
```

```
# それぞれのファイルの中身を less で確認
$ less Human_Bifidobacteriaceae_mod.fasta
$ less Bonobo_Bifidobacteriaceae_mod.fasta
$ less Chimp_Bifidobacteriaceae_mod.fasta
$ less Gorilla_Bifidobacteriaceae_mod.fasta

# それぞれのファイルの中身を cat で確認
$ cat Human_Bifidobacteriaceae_mod.fasta
$ cat Bonobo_Bifidobacteriaceae_mod.fasta
$ cat Chimp_Bifidobacteriaceae_mod.fasta
$ cat Gorilla_Bifidobacteriaceae_mod.fasta

# それぞれのファイルの行数・単語数・バイト数を確認
$ wc Human_Bifidobacteriaceae_mod.fasta
$ wc Bonobo_Bifidobacteriaceae_mod.fasta
$ wc Chimp_Bifidobacteriaceae_mod.fasta
$ wc Gorilla_Bifidobacteriaceae_mod.fasta

# それぞれのファイルの行数・単語数・バイト数をワイルドカードで確認
$ wc *fasta
     102     102   16176 Bonobo_Bifidobacteriaceae_mod.fasta
      18      18    2844 Chimp_Bifidobacteriaceae_mod.fasta
     274     274   43584 Gorilla_Bifidobacteriaceae_mod.fasta
     220     220   34771 Human_Bifidobacteriaceae_mod.fasta
     614     614   97375 total

# 配列名の一覧を grep で確認
$ grep "Human" "Human_Bifidobacteriaceae_mod.fasta"
$ grep "Bonobo" "Bonobo_Bifidobacteriaceae_mod.fasta"
$ grep "Chimp" "Chimp_Bifidobacteriaceae_mod.fasta"
$ grep "Gorilla" "Gorilla_Bifidobacteriaceae_mod.fasta"
```



## 3. ファイルの圧縮と展開

### 3.1. gzip（じーじっぷ）

**1つのファイルしか圧縮できないことに注意**

```sh
# 1つのファイルを圧縮する
$ gzip [圧縮したいファル名]
```

### 3.2. gunzip

```sh
# ファイルを展開（解凍）する
$ gunzip [展開したいファイル名(.gz)]
```

### 3.4. bzip2（びーじっぷつー）

**使い方はgzipと同じで、より圧縮率がよい**

### 3.5. bunzip2

**使い方はgunzipと同じ**

### 3.6. tar（たー）

**tarはまとめるだけで圧縮ではないことに注意**

```sh
# 複数のファイルをまとめる
$ tar cvf [まとめた後のファイル名].tar [まとめたいディレクトリ名]
# 圧縮する
$ gzip [まとめた後のファイル名].tar

# tarでまとめてgzipで圧縮を一度に行う
$ tar zcvf [まとめて圧縮した後のファイル名(.tar.gz)] [まとめたいディレクトリ名]

# gzファイルを展開（解凍）する
$ tar zxvf [まとめて圧縮した後のファイル名(.tar.gz)]

# tarでまとめてbzip2で圧縮を一度に行う
$ tar jcvf [まとめて圧縮した後のファイル名(.tar.bz2)] [まとめたいディレクトリ名]

# bzファイルを展開する
$ tar jxvf [まとめて圧縮した後のファイル名(.tar.bz2)]
```



### 演習3. ここまでのコマンドを使ってみよう

ヒト・ボノボ・チンパンジー・ゴリラの腸内細菌を比較した研究 [Moeller, A. H., Caro-Quintero, A., Mjungu, D., Georgiev, A. V., Lonsdorf, E. V., Muller, M. N., ... & Ochman, H. (2016). Cospeciation of gut microbiota with hominids. *Science*, *353*(6297), 380-382.] のデータの一部を改変して利用

```sh
# ディレクトリを作成する
$ mkdir dir2

# fasta形式のファイルを全てコピーする
$ cp *.fasta dir2

# 更新日時を確認
$ ls -cl dir2/

# gzip で圧縮を試みる
$ gzip dir2
gzip: dir2 is a directory

# tar でまとめる
$ tar cvf dir2.tar dir2

# gzip で圧縮する
# dir2.tar がなくなることに注目
$ gzip dir2.tar

# 展開する
# dir2.tar.gz がなくなることに注目
$ gunzip dir2.tar.gz

# tarでまとめてgzipで圧縮を一度に行う
$ tar zcvf dir2.tar.gz dir2

# tarでまとめてbzip2で圧縮を一度に行う
# dir2 がなくならないことに注目
$ tar jcvf dir2.tar.bz2 dir2

# それぞれのファイルの行数・単語数・バイト数をワイルドカードで確認
$ wc dir2.tar*
     618     743  110080 dir2.tar
      20      92    4692 dir2.tar.bz2
      16     131    5836 dir2.tar.gz
     654     966  120608 total

# tarで展開する
# dir2 が上書きされること・圧縮ファイルは残ることに注目
$ tar zxvf dir2.tar.gz
$ tar jxvf dir2.tar.bz2

# 更新日時を確認
$ ls -cl dir2/
```



## 4. パイプ ( | ) とリダイレクト ( > )

### 4.1. パイプ ( | )

**コマンドの出力を別のコマンドの入力として渡すことができる**

### 4.2. リダイレクト ( > )

**コマンドの出力をファイルに書き込む（上書きされることに注意）**

**上書きをしたくない場合は `>>` で追記する**



**エラーの出力を別のファイルに書き込む**

```sh
$ less xxx.txt
xxx.txt: No such file or directory

$ less xxx.txt > xxx.out
xxx.txt: No such file or directory

$ less xxx.txt > xxx.out 2> err.txt

# 確認
$ less err.txt
```



### 演習4. パイプとリダイレクトを使ってみよう

```sh
# 引数の文字列 "ATGCTTCGATGTAGAAGAGT" を表示する
$ echo "ATGCTTCGATGTAGAAGAGT"
ATGCTTCGATGTAGAAGAGT

# ファイルに出力する
$ echo "ATGCTTCGATGTAGAAGAGT" > DNA.txt

# 確認
$ less DNA.txt

# 引数の文字列 "ATGCTTCGATGTAGAAGAGT" の T を U に変換する
$ sed 's/T/U/g' DNA.txt
AUGCUUCGAUGUAGAAGAGU

# ファイルに出力する
$ sed 's/T/U/g' DNA.txt > RNA.txt

# 確認
$ less RNA.txt

# ここまでのコマンドをパイプでつなぐ
$ echo "ATGCTTCGATGTAGAAGAGT" | sed 's/T/U/g' >> RNA.txt

# 確認
# 追記をしたので、AUGCUUCGAUGUAGAAGAGU が2つ書き込まれているはず。
$ less RNA.txt

# 同様のことをリダイレクトだけで行う
$ sed 's/T/U/g' < DNA.txt >> RNA.txt

# 確認
# さらに追記をしたので、AUGCUUCGAUGUAGAAGAGU が3つ書き込まれているはず。
$ less RNA.txt
```

[EXTRA]
**特定の結果を得るためのコマンドは一つではない**
`perl -pe 's/T/U/g' < DNA.txt >> RNA.txt`
も同じ結果が得られる（はず）



#### [演習4.1.で使うコマンド]

##### 1. echo（えこー）

```sh
# 文字列の出力
$ echo '[文字列]'
```

##### 2. sed（せど）

```
# 命令文に従った処理を文字列に対して行う
# sは置換のコマンドで下記の例では全てのAAAをBBBに置換する
$ sed -e 's/AAA/BBB/g' [処理を行いたいファイル名]
```

### 発展4. gzipで圧縮したファイル

ヒト・ボノボ・チンパンジー・ゴリラの腸内細菌を比較した研究 [Moeller, A. H., Caro-Quintero, A., Mjungu, D., Georgiev, A. V., Lonsdorf, E. V., Muller, M. N., ... & Ochman, H. (2016). Cospeciation of gut microbiota with hominids. *Science*, *353*(6297), 380-382.] のデータの一部を改変して利用

```sh
# cat とリダイレクトで複数のファイルを統合する
$ cat *.fasta > All_Bifidobacteriaceae_mod.fasta

# 確認
$ wc *.fasta
     614     614   97375 All_Bifidobacteriaceae_mod.fasta
     102     102   16176 Bonobo_Bifidobacteriaceae_mod.fasta
      18      18    2844 Chimp_Bifidobacteriaceae_mod.fasta
     274     274   43584 Gorilla_Bifidobacteriaceae_mod.fasta
     220     220   34771 Human_Bifidobacteriaceae_mod.fasta
    1228    1228  194750 total

# 圧縮する
$ gzip All_Bifidobacteriaceae_mod.fasta

# 圧縮したまま中身の確認 (zless)
# less と同じで q でページを閉じる
$ zless All_Bifidobacteriaceae_mod.fasta.gz

# 圧縮したまま指定した文字列が含まれる行を出力 (zgrep)
$ zgrep "Human" "All_Bifidobacteriaceae_mod.fasta.gz"

# コピーを作成
$ cp All_Bifidobacteriaceae_mod.fasta.gz copy.fasta.gz 

# 確認
$ wc *.fasta.gz

# 圧縮したまま統合 (cat)
$ cat *.fasta.gz > cat.fasta.gz

# 確認
# なぜ 192 にならないのかわかりません、すみません
$ wc *.fasta.gz
      18      96    4787 All_Bifidobacteriaceae_mod.fasta.gz
      36     191    9574 cat.fasta.gz
      18      96    4787 copy.fasta.gz
      72     383   19148 total
```

#### [発展4で使うコマンド]

##### 1. zless

**gzipで圧縮したままファイルの中身を確認する**

##### 2. zgrep

**gzipで圧縮したまま指定した文字列が含まれる行を出力する**


## X. おまけ

John H. Gillespie (2004) "Population Genetics: A Concise Guide", 2nd edition

- Answer to Problem 2.2

```python

# pythonを起動する
python

$ python
Python 2.7.5 (default, Nov 16 2020, 22:23:17) 
[GCC 4.8.5 20150623 (Red Hat 4.8.5-44)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>

# pythonを終了する
exit() #もしくは Ctrl + D
```

下記のスクリプトを一行ずつ記入していく

（注）スペースの数も大事なので注意

```python
import random
twoN, p = 40, 0.2
print 0, p
for generation in range(1, 100):
	numberOfA1 = 0
	for trial in range(0, twoN):
		if random.random() < p:
			numberOfA1 += 1
	p = float(numberOfA1) / twoN
	print generation, p
```

**実行結果**
```python
>>> import random
>>> twoN, p = 40, 0.2
>>> print 0, p
0 0.2
>>> for generation in range(1, 100):
...     numberOfA1 = 0
...     for trial in range(0, twoN):
...             if random.random() < p:
...                     numberOfA1 += 1
...     p = float(numberOfA1) / twoN
...     print generation, p
... 
1 0.15
2 0.3
3 0.35
4 0.325
5 0.375
6 0.325
7 0.55
8 0.675
9 0.675
10 0.725
.
.
.
.
88 0.6
89 0.525
90 0.525
91 0.575
92 0.55
93 0.625
94 0.6
95 0.625
96 0.7
97 0.7
98 0.7
99 0.575
```

- ここまでのことが `python` を起動しなくてもできる
```bash
touch gillespie22.py

echo "import random" >> gillespie22.py
echo "twoN, p = 40, 0.2" >> gillespie22.py
echo "print 0, p" >> gillespie22.py
echo "for generation in range(1, 100):" >> gillespie22.py
echo -e "\tnumberOfA1 = 0" >> gillespie22.py
echo -e "\tfor trial in range(0, twoN):" >> gillespie22.py
echo -e "\t\tif random.random() < p:" >> gillespie22.py
echo -e "\t\t\tnumberOfA1 += 1" >> gillespie22.py
echo -e "\tp = float(numberOfA1) / twoN" >> gillespie22.py
echo -e "\tprint generation, p" >> gillespie22.py
```

**実行**
```bash
$ python gillespie22.py > result.txt
$ less result.txt

0 0.2
1 0.125
2 0.2
3 0.2
4 0.225
5 0.225
6 0.225
7 0.3
8 0.275
9 0.325
10 0.3
.
.
.

$ tail result.txt
.
.
.
90 0.0
91 0.0
92 0.0
93 0.0
94 0.0
95 0.0
96 0.0
97 0.0
98 0.0
99 0.0
```

- 10回繰り返す

```bash
$ for i in {1..10};do python gillespie22.py > result_$i.txt;done

$ ls result_*

result_1.txt   result_2.txt  result_4.txt  result_6.txt  result_8.txt
result_10.txt  result_3.txt  result_5.txt  result_7.txt  result_9.txt
```





