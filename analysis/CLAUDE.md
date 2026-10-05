# analysis/ — Python R&D pipeline

- Python 3.11+. Pin every dependency in `requirements.txt`.
- Data lives in `analysis/data/` (gitignored). Never commit images or weights.
- Scripts, not notebooks.
- Every model must export to ONNX using ops supported by ONNX Runtime mobile.
- Measure, don't guess: each detector writes precision/recall on the labeled test set to `analysis/reports/` (small text files, committed).
- A text-check failure must never be masked by another flag (see RESEARCH.md, known failure mode).
