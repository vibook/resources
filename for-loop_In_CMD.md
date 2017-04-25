### for-loop in Command Line

example 1
```
$ programX sample01.txt
$ programX sample02.txt
$ programX sample03.txt
```
```
$ for file in sample*.txt ; do programX $file;done
```
example 2
```
$ bowtie2 -x reference -1 sample01_R1.fastq.gz -2 sample01_R2.fastq.gz -S sample01.sam 2> sample01.out
$ bowtie2 -x reference -1 sample02_R1.fastq.gz -2 sample02_R2.fastq.gz -S sample02.sam 2> sample02.out
```
```html
$ for x in *R1.fastq.gz; do bowtie2 -x reference -1 $x -2 ${x%_R1*}_R2.fastq.gz -S ${x%_R1*}.sam 2> ${x%_R1*}.out ; done
```

출처: [메타지노믹스](http://metagenomics.tistory.com/entry/커맨드라인에서-for문-사용하기) 
