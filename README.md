# Knowledge Distillation of Large Language Models for Bio-species Information Extraction. (still  under development...........)

[![arXiv](https://img.shields.io/badge/arXiv-2403.15430-B31B1B.svg)](https://arxiv.org/abs/2403.15430)

<h3>Overview</h3>
Large language models (LLM) are known for their vast knowledge coverage. But how much of that knowledge is relevant or accurate for extracting specific information regarding biological species such as amphibians, arthropods, birds, fishes, etc.? In this project, we set out to answer this question. 

We leverage a state-of-the-art LLM (i.e., GPT-4) and distill its knowledge to create datasets for both named entity recognition (NER) and relation extraction (RE).

<h3>The Dataset</h3>
Two separate datasets, one for NER and another for RE were created. Each consists of 1.8K sentences. 
<h4>NER Dataset</h4>
The tags are in **BIO** format. The named entities (NE) covered in this dataset are: **SPECIES, HABITAT, FEEDING, BREEDING**. 

Here is the list of BIO tags:
```
list_of_BIO_tags = { 'B-BREEDING', 'I-BREEDING', 'B-FEEDING', 'I-FEEDING', 'B-HABITAT', 'I-HABITAT', 'B-SPECIES', 'I-SPECIES', 'O'
                     }
```
And the format of the NER data is as follows:
***

```
{ 
'tokens': {"0": ["Smoothtooth", "blacktip", "shark", "or", "Carcharhinus", "leiodon", "live", "in", "warm", "coastal", "waters", "particularly", "in", "the", "Indo-Pacific", "region"], ...},
 'tags': {"0": ["B-SPECIE", "I-SPECIE", "I-SPECIE", "O", "B-SPECIE", "I-SPECIE", "O", "O", "O", "O", "O", "O', "O", "O", "O" "O"], ...}
 }
```
***
The two dictionaries `label2id` and `id2label` are shown below: 

Dictionary One: `label2id`
```
labels_to_ids = {
    'B-BREEDING': 0,
    'B-FEEDING': 1,
    'B-HABITAT': 2,
    'B-SPECIES': 3,
    'I-BREEDING': 4,
    'I-FEEDING': 5,
    'I-HABITAT': 6,
    'I-SPECIES': 7,
    'O': 8
}
```
Dictionary Two: `id2label`
```
ids_to_labels = {v: k for k, v in labels_to_ids.items()}
 ```
 ***
<h4>Relation Extraction Data</h4>
We deployed GPTP-4 to generate information about the species' habitats, feeding, and reproduction patterns. The three primary relation classes in our data include: `live_in`, `feed_on`, and `breed_by` classes. 

Here is our RE class to id dictionary:
```
RE_labels = {
    'live_in' : 0,
    'feed_on': 1,
    'breed_by': 2,
    'other': 3,
}
```

To develop a usable RE dataset, we apply the formatting introduced in the paper **Matching the Blanks: Distributional Similarity for Relation Learning**, whose link is [here](https://github.com/jpablou/Relation-Extraction-using-Matching-the-Blanks-methodology-via-Google-BERT-domain-adaptation).

Specifically, we introduce unique `markers` [E1] and [/E1] around the first entity, together with  [E2] and [/E2] around the second entity, in a sentence comprising one relation and two entities (E1 and E2).
For example, in the sentence "Holy mountain salamander feed on insects", the relation is "feed on" and the two entities are "Holy mountain salamander" (i.e., E1) and insects (i.e., E2)

RE dataset format is shown below:
```
[E1]Holy mountain salamander[/E1] feed on [E2]insects[/E2]
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

