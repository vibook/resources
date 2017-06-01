#### Fasta file parsing

```
from Bio import SeqIO
for seq_record in SeqIO.parse("ls_orchid.fasta", "fasta"):
  print(seq_record.id)
  print(repr(seq_record.seq))
  print(len(seq_record))
```
sample file : (ls_orchid.fasta)[https://raw.githubusercontent.com/biopython/biopython/master/Doc/examples/ls_orchid.fasta]

#### GenBank file parsing
```
from Bio import SeqIO
for seq_record in SeqIO.parse("ls_orchid.fasta", "fasta"):
  print(seq_record.id)
  print(repr(seq_record.seq))
  print(len(seq_record))
```
sample file : (ls_orchid.gbk)[https://raw.githubusercontent.com/biopython/biopython/master/Doc/examples/ls_orchid.gbk]

출처 : [생물정보학자의 블로그](http://korbillgates.tistory.com/72)
