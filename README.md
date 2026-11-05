# AI Content Engine: portfolio archive

> **Status: archived portfolio artefact.** This repository documents an early (version 0) design for a claim-aware product-content pipeline. It is no longer developed here.

Active work on this idea has moved to **Satya**, a claim-safe beauty listing engine for Indian D2C brands, which is developed in a private repository. Rule sets, prompts and lexicons are not published.

## What this was

A seven-step design that turns raw product data into reviewable marketing assets, grounded in a structured **Product Truth** record:

1. Product input and normalisation into a Product Truth object
2. Product description generation from that record
3. Competitor marketing intake (manually collected or scraped records)
4. Pattern analysis (saturated angles and whitespace)
5. Campaign direction generation
6. Channel-specific asset generation
7. Human review before anything is used

Three ideas carried the design: facts come only from the Product Truth record, competitor material is evidence of patterns and not copy to imitate, and a person reviews every output.

## What this is not

- Not a working product. There is no running code here, only documents.
- Not a compliance tool. Nothing in this repository certifies that any copy meets a regulation. Any claim-risk wording in the documents is illustrative.
- The worked example uses an anonymised retail product description.

## Contents

| File | Description |
|---|---|
| `index.html` | One-page overview of the pipeline |
| `ai_content_engine_prd.md` | Product requirements for the version 0 prototype |
| `ai_content_engine_build_prompt.md` | Build brief for the prototype |
| `marketing_pipeline_spec.md` | Marketing-content stage specification |
| `overall_pipeline_summary.md` | End-to-end summary of the pipeline |
| `product_description_comparison.md` | Worked example: original vs refined description (anonymised) |
| `AI_Content_Engine_Pipeline_Presentation.pdf` | Seven-step overview presentation |
| `AI_Content_Engine_Portfolio_spec doc.docx` | Portfolio summary document |

## Author

Yaswanth Rahul Yarlagadda, Generative AI Engineer, Stockholm, Sweden.
