# ICDAR 2023 Competition on Robust Layout Segmentation in Corporate Documents

## Introduction

This competition challenges you to advance the research in accurately segmenting the layout in a very broad range of document styles and domains. 

![Complex layouts](figures/complex_pages_with_source_v2.png){ align=left width="300" }

Converting documents into a machine-processable format is an on-going challenge due to their huge variability in formats and complex structure. Recovering the layout structure and content from documents has remained a key problem since decades, and is as relevant as ever in 2023. To this date, a highly generalising model for structure and layout understanding has yet to be achieved. 


To raise the bar over previous competitions, we propose our newly published, human-annotated [DocLayNet](https://github.com/DS4SD/DocLayNet) data-set as the base for a new challenge on various documents from corporate, technical and law domains.

## Task and resources

We invite you to develop a model that can accurately segment the layout components in document pages as bounding boxes on a competition data-set we provide. The layout prediction accuracy you achieve with your solution will be evaluated on this dataset with our human-annotated layout ground-truth. Code submissions are not required. Find the details [here](/task).

We highly recommend you to use our recently published DocLayNet dataset for training and internal validation. DocLayNet is highly diverse in layout coverage, and includes Financial reports, Patents, Manuals, Laws, Tenders and Technical Papers. It is human-annotated with 11 distinct layout class labels. Added value for model development is provided through the original PDF pages and a paired JSON representation of the text cells.

## Schedule

This competition starts on Dec. 19th, 2022 and closes on March 20th, 2023. The detailed schedule is [here](/schedule). 

## Participation

Everyone is welcome to participate in this competition. To ensure fairness, we require teams to abide the [participation rules](/rules).