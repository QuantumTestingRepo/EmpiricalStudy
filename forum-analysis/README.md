# Forum Analysis



This directory contains the dataset and annotation materials used in our forum analysis. The dataset consists of **2,740 posts** collected from three online discussion forums:

* Quantum Computing Stack Exchange (**QCSE**)
* Stack Overflow (**SO**)
* Computer Science Stack Exchange (**CSSE**)

The collected posts were analyzed at two levels. 
First, all 2,740 posts were classified according to their primary discussion concept. 
Second, the 622 posts related to Quantum Software Testing (QST) were further annotated using 
fine-grained QST subtopic labels.

## Directory Structure

```text
Forum-Analysis/
├── 2740_concept_labeled_posts.xlsx
├── 622_subtopic_labeled_posts.xlsx
├── subtopic_definition.txt
└── README.md
```

## File Descriptions

### `2740_concept_labeled_posts.xlsx`

This file contains all **2,740 extracted forum posts**, 
each annotated with one of four concept labels. The `Concept` column records the final agreed label determined by two annotators.

* `Theoretical`, annotated with label "a".
* `Practice`, annotated with label "b".
* `Learning`, annotated with label "c".
* `Error`, annotated with label "d".



### `622_subtopic_labeled_posts.xlsx`

This file contains the **622 posts identified as relevant to QST topics**. Each post is annotated with a fine-grained QST subtopic label.
The `Sublabel` column records the final agreed annotation determined by two annotators.

### `subtopic_definition.txt`

This file provides the detailed definitions of the QST topics and subtopics used to annotate the 622 QST-related posts. It serves as the annotation schema for interpreting the values in the `sublabel` column.

## Annotation Process

Each post was independently examined by two annotators. Disagreements were discussed and resolved to obtain a final agreed annotation. The resulting consensus labels are reported in:



| Annotation Level               | Number of Posts | Final Label Column    |
|--------------------------------| --------------: |-----------------------|
| Concept-level classification   |           2,740 | `Concept`             |
| QST subtopic & Concept classification |             622 | `Sublabel`, `Concept` |

