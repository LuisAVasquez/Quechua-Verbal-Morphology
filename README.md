# Quechua-Verbal-Morphology
A Grammar for the Verbal Morphology of Cuzco and Ayacucho Quechua written as a  Finite State Transducer in PyFOMA


## Details
- To extract the lemmas from the Unimorph dataset for Cuzco and Ayacucho Quechua, run the notebook `lemmatize_verbs`
- The definition of the Grammar in PyFOMA can be found in the notebook `pyfoma_grammar`.
- Executing that notebook produces the grammar

## Overview of the implementation

1. lemmas are extracted from the dataset
2. A prefix symbol and the tagsets are added to the lemmas
3. All suffixing tagsets are rewriten using their corresponding suffixes
4. The prefix symbol is rewritten for those tagsets corresponding to circumfixes
5. The tagsets for circumfixes are rewritten using their corresponding endings
6. The remainin instances of the prefix symbol are deleted



For example, consider the verbs _mikuy_ (to eat), _rimay_ (to speak), and _munay_ (to want).

| 1 | mikuy                     | rimay                         | munay                        |
|---|---------------------------|-------------------------------|------------------------------|
| 2 | [Prefix]mikuy[V;PRS;1;SG] | [Prefix]rimay[V;IMP;NEG;2;PL] | [Prefix]munay[V;PST;FH;3;SG] |
| 3 | [Prefix]miku**ni**        | [Prefix]rimay[V;IMP;NEG;2;PL] | [Prefix]muna**rqan**         |
| 4 | [Prefix]mikuni            | **ama**rimay[V;IMP;NEG;2;PL]  | [Prefix]munarqan             |
| 5 | [Prefix]mikuni            | amarima**ychikchu**           | [Prefix]munarqan             |
| 6 | mikuni                    | amarimaychikchu               | munarqan                     |


## Results

> 99.3% of the inflections from the Unimorph dataset where correctly generated by this grammar!
