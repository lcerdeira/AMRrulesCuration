We need to be able to encode the following types of AMR variants:
- Gene detected
- Amino acid substitution or insertion
- Nucleotide substitution or insertion
- Gene truncated
- Mutation in promoter region (substitution, deletion or insertion, including insertion sequences)
- Allelic or gene copy number changes
- Low frequency variants

Where possible we wish to encode the mutations in a HGVS compliant standard. 

Specific examples of each AMR variant are shown below, with proposed mutation specifications and variation types for each:

| ID     | gene   | mutation           | variation type              | drug          | category  |
|--------|--------|--------------------|-----------------------------|---------------|-----------|
| KLE001 | blaSHV | -                  | Gene presence detected      | ampicillin    | wt R      |
| KLE002 | gyrA   | p.Ser83Tyr         | Protein variant detected    | ciprofloxacin | nwt I     |
| KLE003 | parC   | pSer80Ile          | Protein variant detected    | ciprofloxacin | nwt I     |
| KLE004 | ompK36 | c.C25T             | Nucleotide variant detected | meropenem     | nwt S     |
| KLE005 | ompK36 | p.114_115insGlyAsp | Protein variant detected    | meropenem     | nwt I     |
| KLE006 | mgrB   | p.1~101            | Gene truncation detected    | colistin      | nwt R     |
| KLE007 | qnr    | -                  | Gene presence detected      | ciprofloxacin | nwt I     |
| NGO001 | mtrR   | -                  | Gene truncation detected    | macrolides    | nwt R     |
| ECO001 | ampC   | c.C-11T            | Promoter variant detected   | cephalosporin | nwt R     |
| ECO002 | ampC      | c.-14_-13insGT        | Promoter variant detected                      | cephalosporin           | nwt R  |
| ACI001 | blaOXA-58 | c.-35~1ins[-ISAba125] | Promoter variant detected                      | cephalosporin           | nwt R  |
| NGO002 | 23S rDNA  | c.A2045G{3}           | Nucleotide variant detected in multi-copy gene | azithromycin            | nwt R  |
| ECO003 | blaTEM    | c.{2}                 | Gene copy number variant detected              | piperacillin+tazobactam | nwt R  |


_Syntax explanation:_
- Gene and protein start sites are position 1
- Ranges for known mutations are specified as inclusive_exclusive
- Wildcard ranges are specified as inclusive~exclusive

`p.Ser83Tyr`: change to protein sequence from Ser to Tyr at codon 83

`c.C25T`: change to nucleotide coding region from C to T at nucleotide position 25

`p.114_115insGlyAsp`: change to protein sequence, with an insertion of amino acids Gly and Asp between codons 114 and 115

`p.1~101`: truncation (of any kind) anywhere in the first 100 amino acids of the protein sequence

`c.C-11T`: change to nucleotide sequence from C to T, 11 bases upstream of the start site for the gene.

`c.-14_-13insGT`: insertion of nucleotides GT between positions -14 and -13, upstream of the start site of the gene

`c.-35~1ins[-ISAba125]`: insertion of ISAba125, in reverse orientation (-1), anywhere between 35 bases upstream of the start site, and the beginning of the gene coding sequence

`c.A2045G{3}`: substitution of A to G at position 2045 of the gene. This mutation must occur in minimum 3 copies

`c.{2}`: gene needs to be present with a minimum of 2 copies

**How to deal with combinatorial rules?** 

Combinatorial rules should be defined using logic nomenclature, using the rule identifiers for the individual rules.

| ID     | gene                       | mutation | variation type | drug          | category  |
|--------|----------------------------|----------|----------------|---------------|-----------|
| KLE010 | KLE002 & KLE003            | -        | Combination    | ciprofloxacin | nwt R     |
| KLE011 | (KLE002 | KLE003) & KLE007 | -        | Combination    | ciprofloxacin | nwt R     |


