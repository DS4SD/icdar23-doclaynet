# Task

![Complex layouts](figures/explain_pdf_cluster.png){ align=left width="400" }

You are invited to advance the research in accurately segmenting the layout on a broad range of document styles and domains. To achieve this, we challenge you to develop a model that can correctly identify and segment the layout components in document pages as bounding boxes on a competition data-set we provide.

## Training resources

In our recently published [DocLayNet](https://github.com/DS4SD/DocLayNet) dataset, which contains 80k+ human-annotated document pages exposing diverse layouts, we define 11 classes for layout components (paragraphs, headings, tables, figures, lists, mathematical formulas and several more). We encourage you to use this dataset for training and internal evaluation of your solution.
Further, you may consider any other publicly available document layout dataset for training (e.g. [PubLayNet](https://github.com/ibm-aur-nlp/PubLayNet), [DocBank](https://github.com/doc-analysis/DocBank)).

!!! tip 
        DocLayNet provides not only bitmap page samples and COCO bounding-box annotations, but also the original PDF files and paired JSON with the digital text-cells. This may support you in exploring solving the problem using language and vision with multimodal approaches.
        
 
## Evaluation

### Competition data-set

To assess the layout segmentation performance of your model, we provide a *competition data-set* of 498 new pages in the same manner as [DocLayNet](https://github.com/DS4SD/DocLayNet). This competition data-set includes a balanced mix of corporate document samples as shown below. The new `others` category provides samples which expose additional layouts that fall out of the DocLayNet layout distribution.

| **Document category** 	| **Sample count** 	|
|-----------------------	|------------------	|
| reports               	| 293              	|
| manuals               	| 114              	|
| patents               	| 48               	|
| others                	| 43               	|
| **total**             	| **498**          	|



For the purpose of testing your submissions on the EvalAI platform without restrictions, we also provide a *development dataset*  with only 20 samples.

#### Dataset format

The competition data-set provides PNG images (1025 x 1025 px) of the pages and paired JSON files with the text cell content and bounding-boxes. For details, please refer to the [DocLayNet documentation](https://github.com/DS4SD/DocLayNet#data-format-details).

```
├── coco.json
├── PNG
│   ├── <hash>.png
│   ├── ...
├── JSON
│   ├── <hash>.json
│   ├── ...
```

!!! note
		The provided `coco.json` only contains the definition of images and the class label map (called `categories` in COCO terms). The annotation ground-truth is ommitted.
		
		**Please keep in mind that it is _not allowed_ to create ground-truth for the competition data-set and train your model on it.**


#### Downloads

| **Asset**           	| **Download link** 	|
|---------------------	|-------------------	|
| Competition dataset (498 pages)	| [TBA]()              	|
| Development dataset (20 pages)	| [TBA]()              	|


### Evaluation Metric

Your submissions on our [EvalAI challenge](https://eval.ai/web/challenges/challenge-page/1923/) will be evaluated using the Mean Average Precision (mAP) @ Intersection-over-Union (IoU) [0.50:0.95] metric, as used in the [COCO](https://cocodataset.org/) object detection competition.  In detail, we will calculate the average precision for a sequence of IoU thresholds ranging from 0.50 to 0.95 with a step size of 0.05. This metric is computed for every document category in the competition-dataset. Then the mean of the average precisions on all categories is computed as the final score.

### Submission 

We ask you to upload a JSON file in [COCO results format](https://cocodataset.org/#format-results) [here](https://eval.ai/web/challenges/challenge-page/1923/submission), with complete layout bounding-boxes for each page sample. The given `image_id`s must correspond to the ones we publish with the competition data-set's `coco.json`. For each submission you make, the computed mAP will be provided for each category as well as combined. The [leaderboard](https://eval.ai/web/challenges/challenge-page/1923/leaderboard/4545/Total) will be ranked based on the overall mAP.

#### Example submission snippet

```js
[
  {
    "bbox": [  // bounding-box in COCO format (x,y,w,h)
      105,
      290,
      500,
      120
    ],
    "category_id": 4, // ID of label class for this bounding-box. Find the `categories` dictionary in the coco.json. Must resolve to one of [Caption, Footnote, Formula, List-item, Page-footer, Page-header, Picture, Section-header, Table, Text, Title].
    "image_id": 0, // ID of dataset sample that this annotation is referring to, find the `images` dictionary in the coco.json
    "score": 0.77
  },
  {
    "bbox": [
      602,
      302,
      354,
      30
    ],
    "category_id": 4,
    "image_id": 0,
    "score": 0.94
  },
  ...
```

