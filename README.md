 [戻る](https://github.com/PM2951/Python-forMAC)    

# Biopython を使った DNA/遺伝子情報の練習問題

[Biopython入門](https://biomedicalhacks.com/2020-05-12/biopython-basic-1/)を参考に以下の問題を解いてください。

解説のない用法もあるので、適宜Googleで検索してください

---

## 練習用ファイル: sample.fa と sequence.gb

以下の 2 つのファイルを作成し、同じフォルダに保存しておくと、複数の問題で共通に利用できます。  
テキストファイルに内容をコピペして、それぞれファイル名で保存する。

**※ sample.fa と sequence.gbは、pythonの実行ファイルがあるフォルダに保存する**

ファイル名:

```text
sample.fa
```

内容:

```fasta
>geneA_example
ATGCGTACGTTAGCGTACGTTAG
>geneB_example
GGGCGCGCGTTTAAACCCGGGTT
>geneC_example
ATATATATATATATATATATAT
```


ファイル名:

```text
sequence.gb
```

内容:

```text
LOCUS       SYNTH1                90 bp    DNA     linear   SYN 01-JAN-2000
DEFINITION  Synthetic example DNA sequence for Biopython practice.
ACCESSION   SYNTH00001
VERSION     SYNTH00001.1
KEYWORDS    .
SOURCE      synthetic DNA construct
  ORGANISM  synthetic DNA construct
            other sequences; artificial sequences.
FEATURES             Location/Qualifiers
     source          1..90
                     /organism="synthetic DNA construct"
                     /mol_type="other DNA"
                     /note="example sequence for teaching"
     gene            1..90
                     /gene="example_gene"
     CDS             1..90
                     /gene="example_gene"
                     /codon_start=1
                     /product="example protein"
                     /translation="MAIVMGR*KGAR*MAIVMGR*KGAR*MAIV"
ORIGIN
        1 atggccattg taatgggccg ctgaaagggt gcccgataga tggccattgt aatgggccgc
       61 tgaaagggtg cccgatagat ggccattgta
//
```

---


### 問題1：Seq オブジェクトの作成と長さの確認

**使用データ**
DNA 配列:

```text
ATGCGTACGTTAG
```

**課題**

1. 上記の DNA 配列から `Seq` オブジェクトを作成しなさい。
2. 作成した配列をそのまま表示しなさい。
3. 配列の長さ（塩基数）を表示しなさい。

---

### 問題2：スライスによる部分配列の取得

**使用データ**
DNA 配列:

```text
ATGCGTACGTTAG
```

**課題**

1. 先頭 3 塩基のみを取り出して表示しなさい。
2. 最後の 4 塩基のみを取り出して表示しなさい。
3. 3 塩基目から 8 塩基目までの部分配列を取り出して表示しなさい（インデックスを用いること）。
4. 配列を逆順にした配列を表示しなさい。

---

### 問題3：GC 含量の計算（手計算と関数）

**使用データ**
FASTA ファイル:

```text
sample.fa
```

に含まれる次の 2 配列:

```text
geneA_example: ATGCGTACGTTAGCGTACGTTAG
geneB_example: GGGCGCGCGTTTAAACCCGGGTT
```

これら 2 配列をそれぞれ `seq1`, `seq2` としてとりだしなさい。

**課題**

1. 各配列について、`G` と `C` の文字数を数え、GC 含量（GC%）を計算しなさい。


---

### 問題4：相補鎖と逆相補鎖の取得

**使用データ**
DNA 配列:

```text
AGGTCGATTA
```

**課題**

1. 上記 DNA 配列から `Seq` オブジェクトを作成しなさい。
2. 相補鎖を求めて表示しなさい。
3. 逆相補鎖を求めて表示しなさい。
4. 元の配列・相補鎖・逆相補鎖の 3 つをわかりやすく表示しなさい。

---

### 問題5：転写と翻訳

**使用データ**
コーディング鎖（簡略化した ORF を想定）としての DNA 配列:

```text
ATGGCCATTGTAATGGGCCGCTGAAAGGGTGCCCGATAG
```

**課題**

1. 上記 DNA から mRNA 配列を転写して表示しなさい。
2. この DNA 配列を翻訳し、アミノ酸配列を表示しなさい。
3. DNA 配列の長さを求め、3 の倍数になっているかどうかを確認しなさい。
4. スタートコドンとストップコドンがどこにあるか、配列上の位置（インデックス）を調べなさい。

---

### 問題6：FASTA の各配列の ID と長さの表示

**使用データ**
FASTA ファイル:

```text
sample.fa
```

**課題**

1. `sample.fa` を読み込み、各レコードを順に表示しなさい。
2. 各レコードについて、ID と配列長（塩基数）を表示しなさい。

---

### 問題7：GC 含量が高い配列だけを抽出

**使用データ**
FASTA ファイル:

```text
sample.fa
```

**課題**

1. GC% が 50%以上 の配列だけを抽出し、その ID と GC% を表示しなさい。
2. 1の条件に合致した配列の塩基長を表示しなさい。

---


### 問題8：複数の DNA 配列を SeqRecord にまとめて FASTA に書き出す

**使用データ**
3 つの DNA 配列と ID:

```text
id: gene1, seq: ATGAAATTTGGGCCC
id: gene2, seq: ATGCCCCCCGGGTTTAA
id: gene3, seq: ATGTTTAAACCCGGG
```

**課題**

1. 各 DNA 配列から `Seq` オブジェクトを作成し、それぞれを `SeqRecord` として定義しなさい。ID は上記の通りとする。
2. 3 つの `SeqRecord` をリストにまとめなさい。
3. それらを 1 つの FASTA ファイル `my_genes.fa` に書き出しなさい。
4. 書き出した `my_genes.fa` を読み込み、ID と配列長を表示して、正しく保存されているか確認しなさい。


---

### 問題9：GenBank ファイルの基本情報を取得

**使用データ**
GenBank ファイル:

```text
sequence.gb
```

**課題**

1. `sequence.gb` を読み込み、`SeqRecord` オブジェクトとして取得しなさい（1 レコードのみ入っていると仮定する）。
2. そのレコードの ID、説明文（description）、配列長を表示しなさい。
3. GenBank ファイル中の機能アノテーション（features）がいくつあるか数え、個数を表示しなさい。

---

### 問題10：GenBank → FASTA 変換と GC 含量の表示

**使用データ**
GenBank ファイル:

```text
sequence.gb
```

**課題**

1. `sequence.gb` を読み込み、その内容を FASTA 形式ファイル `sequence.fa` に変換して保存しなさい（1つ以上のレコードが入っている場合にも対応すること）。
2. 変換して得られた `sequence.fa` を読み込み、各レコードについて ID、配列長、GC% を表示しなさい。
3. すべてのレコードの GC% の平均値を計算して表示しなさい。

---

