# Results reported in the supplied paper

Source: `1810.pdf`, *An Attention Based Deep Learning Approach for Classification of Potato and Tomato Blight Leaves*. Values below are transcriptions of the manuscript tables, not results recomputed from this package. The PDF itself is not included in the repository package.

## Table II: accuracy

| Crop | Epochs | Training accuracy (%) | Validation accuracy (%) |
| --- | ---: | ---: | ---: |
| Potato | 50 | 99.47 | 99.25 |
| Tomato | 50 | 95.75 | 93.98 |

## Table III: loss

| Crop | Epochs | Training loss | Validation loss |
| --- | ---: | ---: | ---: |
| Potato | 50 | 0.0248 | 0.036 |
| Tomato | 50 | 0.1182 | 0.1355 |

## Table IV: classification metrics

| Crop | Precision | Recall | F1-score |
| --- | ---: | ---: | ---: |
| Potato | 0.93 | 0.92 | 0.92 |
| Tomato | 0.93 | 0.92 | 0.93 |

Table IV does not specify its metric-averaging convention in the extracted table. Do not infer macro/weighted averaging or tie these values to the selected 300-image notebook output without the original evaluation provenance.

The paper's case-study prose refers to test sets while Table II labels the accuracy as validation accuracy. This repository retains the table's terminology rather than upgrading it to independently held-out test performance.

See `historical_outputs/` for separately preserved notebook text and `../docs/CODE_REVIEW.md` for the differences. Tomato code was not supplied, and the model file used by later evaluation cells was not supplied.
