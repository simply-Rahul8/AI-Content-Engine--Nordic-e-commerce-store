# Build Prompt for Coding Agent

Build a quick working prototype of an **AI Content Engine for beauty e-commerce** as a Python app using **Streamlit** and **Pydantic**.

## Goal
The app should support an end-to-end workflow:
1. Accept raw cosmetic product input.
2. Convert it into a structured **product truth object**.
3. Generate a structured **product description**.
4. Accept manually fed **competitor campaign records**.
5. Analyze competitor messaging patterns.
6. Propose **campaign directions**.
7. Generate **marketing assets** for a selected direction.

This is a **version 0 prototype**, so do **not** build live web scraping, database auth, deployment, or production integrations. Assume competitor records are manually pasted or uploaded as JSON.

## Product Principles
- The product description stage is the factual foundation.
- Marketing generation must be grounded in product truth.
- Competitor records are used for pattern analysis, not copying.
- The UI should make every stage visible and editable.
- Keep the app simple, clean, and demo-ready.

## Technical Requirements
- Use Python.
- Use Streamlit for the UI.
- Use Pydantic for data models.
- Organize code cleanly into modules such as `models.py`, `prompts.py`, `services.py`, and `app.py`.
- Make the LLM provider configurable through environment variables.
- Support a fallback mock mode if no API key is present.
- Keep data in memory or in local JSON files only.

## Required Data Models
Implement Pydantic models for:
- `ProductTruth`
- `ProductDescription`
- `CompetitorRecord`
- `PatternAnalysis`
- `CampaignDirection`
- `MarketingAssets`
- `PipelineState`

## UI Requirements
Create a multi-step Streamlit app with these sections:

### 1. Product Input
Form fields:
- brand
- product name
- category
- subcategory
- format
- size
- price (optional)
- ingredients
- benefits
- usage instructions
- free-from claims
- audience notes
- tone constraints
- allowed claims
- disallowed claims

### 2. Product Truth
- Show extracted structured product truth.
- Allow user edits.
- Include a button: `Generate Product Truth`.

### 3. Product Description
Generate and show:
- headline
- positioning line
- about the product
- ingredient highlights
- how to use
- suitable for
- warnings and storage
- specifications

Include a button: `Generate Product Description`.
Allow editing of each section.

### 4. Competitor Campaign Input
Support:
- paste JSON array of competitor records
- optional text area for manual notes
- sample JSON template shown in UI

Each competitor record should support:
- brand
- product_name
- product_category
- channel
- campaign_type
- headline
- subheadline
- body_copy
- cta
- angle_tags
- tone_tags
- claim_tags
- proof_style
- source_url
- date_observed
- notes

### 5. Pattern Analysis
Generate and show:
- dominant angles
- dominant tones
- overused phrases
- common proof styles
- whitespace opportunities
- risk flags

Include a button: `Analyze Competitor Patterns`.

### 6. Campaign Directions
Generate 3 to 5 directions with:
- name
- summary
- fit score
- novelty score
- market overlap
- target segments
- key messages
- proof points to use
- reasons to believe
- watchouts

Include a button: `Generate Campaign Directions`.
Allow selecting one direction.

### 7. Marketing Assets
Generate for selected direction:
- PDP hero headline options
- PDP subheadline options
- category card copy
- social ad variants (hook, body, CTA)
- email subject lines
- email preview texts
- optional landing-page blurbs

Include a button: `Generate Marketing Assets`.
Allow copy/export.

## Prompting Rules
Implement separate prompt templates for:
1. Product truth extraction
2. Product description generation
3. Competitor pattern analysis
4. Campaign direction generation
5. Marketing asset generation

Prompt rules:
- Never invent unsupported product facts.
- Always use product truth as the source of record.
- Treat competitor inputs as pattern evidence, not source copy.
- Avoid aggressive medical or regulatory-risk claims.
- Prefer clear, structured outputs in JSON.
- Generate multiple options where useful.

## Mock Data
Include:
- one prefilled beauty-product example based on a scalp oil / hair treatment
- one sample competitor JSON dataset with at least 3 records

## Output Requirements
The app should allow the user to:
- inspect every intermediate object
- edit generated outputs
- download current pipeline state as JSON
- download product description as Markdown
- download marketing outputs as Markdown

## Nice-to-Have
If fast to implement:
- tabs per step
- status badges for completed sections
- JSON validation errors shown clearly
- side-by-side raw data vs generated output

## What to Avoid
- No overengineered architecture
- No live scraping inside the app
- No database
- No authentication
- No production deployment code
- No unnecessary styling complexity

## Deliverable
Return a complete working prototype codebase with:
- clear file structure
- installation instructions in README
- `.env.example`
- sample data
- runnable Streamlit app

## Quality Bar
The prototype should feel like a serious internal tool demo, not just a single prompt in a textbox. It should show clear separation between product truth, pattern analysis, strategy generation, and asset generation.
