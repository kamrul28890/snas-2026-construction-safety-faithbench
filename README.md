# ConstructionSafety-FaithBench

Clean reproducibility package for the SNAS 2026 short paper:

**ConstructionSafety-FaithBench: Auditing Visual-Evidence Faithfulness in Construction-Safety Vision-Language Models**

Public repository: https://github.com/kamrul28890/snas-2026-construction-safety-faithbench

## What Is Included

- Blind SNAS short-paper and abstract PDFs under `submission/`.
- Copy-paste submission text and final risk checklist under `paper/snas/`.
- Benchmark manifests, safety rules, prompts, schemas, and intervention specs.
- Frozen model outputs and generated score tables used in the paper.
- The 120-row final audit-label layer with explicit A/B audit-pass and adjudication provenance.
- Source code and tests required to validate schemas and regenerate major results.

Raw ConstructionSite images, model weights, local annotator handoff folders, caches, and venue-draft material are not included.

## Headline Numbers

- Audit labels: 120 rows; 108 A/B consensus rows plus 12 returned adjudication decisions.
- Final label distribution: 83 violation, 31 compliant, 6 uncertain.
- Florence grounding accuracy on the audit layer: 18.3%.
- Automated baseline accuracy on the audit layer: 78.3%.
- Targeted evidence-occlusion answer flip rate: 39.2%.
- Matched-random answer flip rate: 9.2%.
- Paired answer-flip difference: 30.0 percentage points.

## Important Provenance Note

The final audit labels should be described as:

`two independent audit passes plus returned adjudication`

or:

`adjudicated audit labels with AI-pass provenance`

Do not describe them as unqualified human ground truth unless an independent human/domain audit replaces or verifies this layer.

## Reproduce Checks

```powershell
pip install -r requirements.txt
python .\experiments\validate_benchmark_specs.py
python .\experiments\validate_annotations.py
python .\experiments\validate_human_audit_batch.py
python .\experiments\validate_model_outputs.py
python .\experiments\validate_intervention_outputs.py
python .\experiments\validate_phase4_outputs.py
python .\experiments\validate_scaleup_manifest.py
pytest .\tests -q
```
