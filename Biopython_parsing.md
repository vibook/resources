#### Fasta file parsing

```
from Bio import SeqIO
for seq_record in SeqIO.parse("ls_orchid.fasta", "fasta"):
  print(seq_record.id)
  print(repr(seq_record.seq))
  print(len(seq_record))
```
sample file : [ls_orchid.fasta](https://raw.githubusercontent.com/biopython/biopython/master/Doc/examples/ls_orchid.fasta)

#### GenBank file parsing
```
from Bio import SeqIO
for seq_record in SeqIO.parse("ls_orchid.fasta", "fasta"):
  print(seq_record.id)
  print(repr(seq_record.seq))
  print(len(seq_record))
```
sample file : [ls_orchid.gbk](https://raw.githubusercontent.com/biopython/biopython/master/Doc/examples/ls_orchid.gbk)

#### Sequence Indexing, Complement and Reverse Complement
```
>>> from Bio.Seq import Seq
>>> from Bio.Alphabet import IUPAC
>>> my_seq = Seq("GATCG", IUPAC.unambiguous_dna)
>>> for index, letter in enumerate(my_seq):
... print(index, letter)
...
0 G
1 A
2 T
3 C
4 G
>>> print(len(my_seq)) 
5
>>> print(my_seq[0])
G
>>> print(my_seq[2])
T
>>> print(my_seq[-1])
G
>>> print(my_seq[1:3])
AT
>>> "AAAA".count("AA")
2
>>> Seq("AAAA").count("AA")
2
>>> my_seq.complement()
Seq("CTAGC", IUPACUnambiguousDNA())
>>> my_seq.reverse_complement()
Seq("CGATC", IUPACUnambiguousDNA())
```

#### GC contents 계산
```
>>> from Bio.Seq import Seq
>>> from Bio.Alphabet import IUPAC
>>> my_seq = Seq('GATCGATGGGCCTATATAGGATCGAAAATCGC', IUPAC.unambiguous_dna)
>>> len(my_seq)
32
>>> my_seq.count("G")
9
>>> 100 * float(my_seq.count("G") + my_seq.count("C")) / len(my_seq)
46.875
```
```
>>> from Bio.Seq import Seq
>>> from Bio.Alphabet import IUPAC
>>> from Bio.SeqUtils import GC
>>> my_seq = Seq('GATCGATGGGCCTATATAGGATCGAAAATCGC', IUPAC.unambiguous_dna)
>>> GC(my_seq)
46.875
```

#### Sequence 객체 더하기
```
>>> from Bio.Seq import Seq
>>> from Bio.Alphabet import generic_dna
>>> my_seq1 = Seq("ACGT", generic_dna)
>>> my_seq2 = Seq("AACC", generic_dna)
>>> my_seq3 = my_seq1 + my_seq2
>>> my_seq3 
Seq('ACGTAACC', DNAAlphabet())

>>> nuc_seq = Seq("GATCGATGC", generic_nucleotide)
>>> dna_seq = Seq("ACGT", IUPAC.unambiguous_dna)
>>> nuc_seq
Seq("GATCGATGC", NucleotideAlphabet())
>>> dna_seq
Seq("ACGT", IUPACUnambiguousDNA())
>>> nuc_seq + dna_seq
Seq("GATCGATGCACGT", NucleotideAlphabet())
```

#### 전사와 번역
```
>>> coding_dna = Seq("ATGGCCATTGTAATGGGCCGCTGAAAGGGTGCCCGATAG", IUPAC.unambiguous_dna)
>>> messenger_rna = coding_dna.transcribe()
>>> messenger_rna
Seq('AUGGCCAUUGUAAUGGGCCGCUGAAAGGGUGCCCGAUAG', IUPACUnambiguousRNA()) 
>>> messenger_rna.translate() 
Seq('MAIVMGR*KGAR*', HasStopCodon(IUPACProtein(), '*'))
```
출처 : [생물정보학자의 블로그](http://korbillgates.tistory.com/72)
