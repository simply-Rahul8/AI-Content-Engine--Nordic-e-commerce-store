# PRD: AI Content Engine Quick Prototype

## Product Name
AI Content Engine Prototype for Beauty E-commerce

## Objective
Build a quick working prototype that takes a single cosmetic product as input, generates a structured product description, accepts manually collected competitor marketing records, analyzes market messaging patterns, proposes campaign directions, and generates channel-specific marketing content. The prototype should demonstrate an end-to-end flow from product truth to competitor-aware marketing outputs while keeping the product description as the factual foundation.

## Problem Statement
Beauty and e-commerce teams often need to create both product descriptions and marketing content for many products across multiple channels. Existing workflows are repetitive, inconsistent, and slow, and they can easily produce generic copy or unsupported claims if content is generated without a stable product-truth layer.

This prototype solves that by creating a two-stage AI workflow:
1. Generate a structured, human-readable, product-faithful description from raw product data.
2. Use that validated product truth plus manually fed competitor campaign records to generate differentiated, reviewable marketing directions and assets.

## Target User
The primary user is an internal content, merchandising, innovation, or AI team member working on beauty-product content for an e-commerce environment. The user is not assumed to be deeply technical, so the prototype should present clear inputs, visible intermediate outputs, and editable final drafts.

## Version Scope
This is a version 0 prototype. It does not need full production scraping, authentication, CMS publishing, or multilingual support. Competitor campaign data will be manually fed into the system after being collected using an external scraping or research tool.

## Goals
- Accept raw cosmetic product data and convert it into a structured product truth object.
- Generate a refined hybrid product description that preserves key facts and improves readability and customer relevance.
- Accept structured competitor campaign inputs.
- Analyze competitor messaging patterns and identify whitespace opportunities.
- Generate 3 to 5 campaign directions.
- Generate draft marketing assets for a selected direction across multiple channels.
- Allow the user to review and regenerate outputs.

## Non-Goals
- Fully automated web scraping inside the app
- Live ad platform integration
- Publishing to production systems
- Fine-tuning custom models
- Automated compliance approval
- Multi-user collaboration

## Core User Flow
1. User enters or pastes raw product information.
2. System normalizes the input into a product truth object.
3. System generates the product description outputs.
4. User reviews and optionally edits the product truth or description.
5. User uploads or pastes structured competitor campaign records.
6. System runs pattern analysis on competitor messaging.
7. System proposes campaign directions.
8. User selects one direction.
9. System generates channel-specific marketing assets.
10. User reviews, edits, copies, or exports the results.

## Functional Requirements

### Module 1: Product Input
The prototype must allow the user to input:
- Brand
- Product name
- Category and subcategory
- Format (serum, oil, cream, mask, etc.)
- Size and optional price
- Core ingredients
- Core benefits
- Usage instructions
- Free-from claims
- Audience notes
- Tone constraints
- Allowed and disallowed claims

### Module 2: Product Truth Generation
The system must convert raw input into a structured product truth object that includes:
- Product identity
- Audience definition
- Core benefits
- Proof points
- Hero ingredients and plain-language roles
- Claims guardrails
- Brand voice rules.

### Module 3: Product Description Generation
The system must generate:
- Headline
- Positioning line
- About the product
- Ingredient highlights
- How to use
- Suitable for
- Warnings and storage
- Specifications / INCI block

The description should be hybrid in tone: clear, commercially useful, and lightly empathetic without becoming overly emotional. It must preserve key product facts and avoid unsupported claim language.

### Module 4: Competitor Campaign Input
The system must accept manually fed competitor records in JSON or form-based entry. Each competitor record should include:
- Brand
- Product name
- Product category
- Channel
- Campaign type
- Headline
- Subheadline
- Body copy
- CTA
- Angle tags
- Tone tags
- Claim tags
- Proof style
- Source URL
- Date observed
- Notes.

### Module 5: Pattern Analysis
The system must analyze competitor records and output:
- Dominant angles
- Dominant tones
- Overused phrases
- Common proof styles
- Whitespace opportunities
- Risk flags around claim style or saturation.

### Module 6: Campaign Direction Generation
The system must generate 3 to 5 candidate directions. Each direction must include:
- Direction name
- One-sentence summary
- Fit score
- Novelty score
- Market overlap level
- Target segments
- Key messages
- Proof points to emphasize
- Reasons to believe
- Watchouts.

### Module 7: Marketing Asset Generation
After a direction is selected, the system must generate:
- PDP hero headlines and sublines
- Category-card copy
- Social ad variants (hook, body, CTA)
- Email subject lines and preview text
- Optional short landing-page blurbs.

## UX Requirements
- Use a simple single-page flow or multi-step wizard.
- Make each stage visible: product input, product truth, product description, competitor input, pattern analysis, directions, and final assets.
- Show intermediate artifacts so the user understands how outputs were produced.
- Make all generated text editable.
- Include regenerate buttons per section rather than one global regenerate.
- Allow JSON import/export where possible.

## Suggested Tech Stack
- Frontend: Streamlit or Gradio for fastest prototype development
- Backend logic: Python
- Data models: Pydantic
- LLM provider: configurable via API
- Storage: in-memory or local JSON files for version 0

## Suggested Data Models
The prototype should implement these core top-level models:
- `ProductTruth`
- `CompetitorRecord`
- `PatternAnalysis`
- `CampaignDirection`
- `MarketingAssets`
- `PipelineState`

## Example Pipeline State
```json
{
  "product_truth": {},
  "product_description": {},
  "competitor_records": [],
  "pattern_analysis": {},
  "campaign_directions": [],
  "selected_direction_id": "",
  "marketing_assets": {}
}
```

## Prompting Requirements
The prototype should use separate prompts for:
- Product truth extraction
- Product description generation
- Competitor pattern analysis
- Campaign direction generation
- Asset generation

The prompts should always treat product truth as the factual source of record, and competitor messaging as pattern evidence rather than copy to imitate.

## Output Quality Requirements
- Preserve core product facts.
- Avoid unsupported medical or cosmetic claims.
- Maintain channel-appropriate length.
- Keep language clear and readable for broad audiences.
- Avoid generic hype phrases.
- Generate multiple options where choice matters.
- Include reasoning metadata where useful.

## Success Criteria
The prototype is successful if a user can:
1. Input a beauty product.
2. Generate a usable structured product description.
3. Feed competitor campaign examples.
4. Receive a meaningful pattern analysis.
5. Select a campaign direction.
6. Generate usable first-draft marketing assets in one session.

## Future Extensions
- Automated competitor scraping inside the product
- Freshness scoring by date observed
- Multilingual generation
- Brand-specific tone presets
- Compliance rules engine
- Export to CMS, PIM, or marketing systems
