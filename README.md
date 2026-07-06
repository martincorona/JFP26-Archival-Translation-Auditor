# JFP26-Archival-Translation-Auditor
**Division:** Digital Strategy Directorate (DSD), Library of Congress
## Overview
This repository contains my summer project evaluating how well different tiers of generative AI models translate 19th-century Spanish archival documents. 

I used the 1848 Treaty of Guadalupe Hidalgo as the core dataset. Because the historical document was legally required to be exact, it features official Spanish and English texts printed side-by-side. This provided a flawless, historically verified "Ground Truth" parallel text to benchmark the models against without the messy inconsistencies found in standard datasets.

## Testing Methodology (LLM-as-a-Judge)
Instead of relying on rigid string-matching scripts (which fail on historical language nuances), I designed a prompt-based evaluation framework. I configured an advanced model to act as an automated semantic grader, feeding it the original 1848 Spanish and the official English translation.

I then passed target translations from three distinct tools into the judge:
1. **Google Translate** (Traditional Machine Translation)
2. **GPT-3.5** (Standard LLM)
3. **GPT-4.0** (Advanced LLM)

The judge was instructed to flag three specific historical translation failures:
1. **Idiomatic Failure:** Literal translations that break formal 19th-century legal nuance.
2. **Temporal Drift:** Modern corporate/bureaucratic jargon that ruins the historical tone.
3. **Fact Alteration:** Hallucinations, dropped data points, or localized names/dates.

## Repository Structure
This repository contains the documentation required to reproduce this evaluation pipeline:
* `evaluation_prompts.md`: The exact system architecture and prompt instructions used to configure the LLM grader.
* `verified_test_cases.md`: The documented results of the pipeline successfully catching real translation errors across all three tested models.

## Impact
This testing process provides a scalable, reproducible blueprint for safely evaluating AI tools for cross-lingual archival research, ensuring the Library can leverage modern technology without risking historical data integrity.
