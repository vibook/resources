### for-loop in Command Line

```
$ programX sample01.txt
$ programX sample02.txt
$ programX sample03.txt
```
```html
<span style="color: green">$ for file in sample*.txt ; do programX $file;done</span>
```

```
$ bowtie2 -x reference -1 sample01_R1.fastq.gz -2 sample01_R2.fastq.gz -S sample01.sam 2> sample01.out
$ bowtie2 -x reference -1 sample02_R1.fastq.gz -2 sample02_R2.fastq.gz -S sample02.sam 2> sample02.out
```
```html
<span style="color: green">$ for x in *R1.fastq.gz; do bowtie2 -x reference -1 $x -2 ${x%_R1*}_R2.fastq.gz -S ${x%_R1*}.sam 2> ${x%_R1*}.out ; done</span>
```

출처: [메타지노믹스](http://metagenomics.tistory.com/entry/커맨드라인에서-for문-사용하기) 
