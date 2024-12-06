# Knowledge Distillation of Large Language Models for Bio-species Information Extraction. (still  under development)

[![arXiv](https://img.shields.io/badge/arXiv-2403.15430-B31B1B.svg)](https://arxiv.org/abs/2403.15430)

<h3>Overview</h3>
Large language models (LLM) are known for their vast knowledge coverage. But how much of that knowledge is relevant or accurate for extracting specific information regarding biological species such as amphibians, arthropods, birds, fishes, etc.? In this project, we set out to answer this question. 

We leverage a state-of-the-art LLM (i.e., GPT-4) and distill its knowledge to create datasets for both named entity recognition (NER) and relation extraction (RE).

<h3>The Dataset</h3>
Two separate datasets, one for NER and another for RE were created. Each consists of 1.8K senetnces. 
The NER dataset is contained in the **HARU_bio_1.json** file. The tags are in **BIO** format. The Topics covered in this dataset are: **SPECIES, HABITAT, FEEDING, BREEDING**. 

***

```
{ 
'tokens': {"0": ["Poco", "Bueno", "was", "a", "American", "Quarter", "Horse", "stallion", "foaled", "April", "10", ",", "1944", "."], "1": ["Formal", "breeds", "often", "considered", "to", "be", "of", "the", "pit", "bull", "type", "include", "the", "American", "Pit", "Bull", "Terrier", ",", "American", "Staffordshire", "Terrier", ",", "American", "Bully", ",", "and", "Staffordshire", "Bull", "Terrier", "."], ... },
 'tags': {"0": ["O", "O", "O", "O", "B-PET", "I-PET", "I-PET", "O", "O", "O", "O", "O", "O", "O"], "1": ["O", "O", "O", "O", "O", "O", "O", "O", "B-PET", "I-PET", "O", "O", "O", "O", "B-PET", "I-PET", "I-PET", "O", "B-PET", "I-PET", "I-PET", "O", "B-PET", "I-PET", "O", "O", "B-PET", "I-PET", "I-PET", "O"], ...}
 }
```
***
The two dictionaries `label2id` and `id2label` are shown below: 

Dictionary One: `label2id`
```
{'B-JOB': 0,
 'B-PET': 1,
 'I-PEOPLENAME': 2,
 'B-PEOPLENAME': 3,
 'I-COUNTRY': 4,
 'O': 5,
 'I-ORG': 6,
 'I-JOB': 7,
 'B-COUNTRY': 8,
 'I-PET': 9,
 'B-ORG': 10}
```
Dictionary Two: `id2label`
```
{0: 'B-JOB',
 1: 'B-PET',
 2: 'I-PEOPLENAME',
 3: 'B-PEOPLENAME',
 4: 'I-COUNTRY',
 5: 'O',
 6: 'I-ORG',
 7: 'I-JOB',
 8: 'B-COUNTRY',
 9: 'I-PET',
 10: 'B-ORG'}
 ```
 ***

Moreover, the RE dataset is of the format below:
```
{ 
'tokens': {"0": ["Poco", "Bueno", "was", "a", "American", "Quarter", "Horse", "stallion", "foaled", "April", "10", ",", "1944", "."], "1": ["Formal", "breeds", "often", "considered", "to", "be", "of", "the", "pit", "bull", "type", "include", "the", "American", "Pit", "Bull", "Terrier", ",", "American", "Staffordshire", "Terrier", ",", "American", "Bully", ",", "and", "Staffordshire", "Bull", "Terrier", "."], ... },
 'tags': {"0": ["O", "O", "O", "O", "B-PET", "I-PET", "I-PET", "O", "O", "O", "O", "O", "O", "O"], "1": ["O", "O", "O", "O", "O", "O", "O", "O", "B-PET", "I-PET", "O", "O", "O", "O", "B-PET", "I-PET", "I-PET", "O", "B-PET", "I-PET", "I-PET", "O", "B-PET", "I-PET", "O", "O", "B-PET", "I-PET", "I-PET", "O"], ...}
 }
```

<h3>Experiments</h3>
We deploy several LLMs for the NER and RE evaluation.

### Citation

If you find this work or dataset helpful in your research, please cite it as follows:

```bibtex
@misc{atuhurra2024distillingnamedentityrecognition,
  title         = {Distilling Named Entity Recognition Models for Endangered Species from Large Language Models}, 
  author        = {Atuhurra, Jesse and Dujohn, Seiveright Cargill and Kamigaito, Hidetaka and Shindo, Hiroyuki and Watanabe, Taro},
  year          = {2024},
  eprint        = {2403.15430},
  archivePrefix = {arXiv},
  primaryClass  = {cs.CL},
  url           = {https://arxiv.org/abs/2403.15430}
}

