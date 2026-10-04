# Submission Info

- Name: Tran Cao Thang
- Student ID: 2A202602520
- Lab: K4-Track02-Day18
- Repository: K4-Track02-Day18-TranCaoThang-2A202602520-Lakehouse-Lab
- GitHub remote: https://github.com/ThangC4T/K4-Track02-Day18-TranCaoThang-2A202602520-Lakehouse-Lab
- Execution path: lightweight local path
- Operating system: Windows
- Python: 3.11.9
- Notebook set: 8 lightweight notebooks in `submission/notebooks/`

## Verification

- `scripts/verify_lite.py`: PASS, 9/9 checks.
- `scripts/generate_data_lite.py`: generated 200,000 Bronze LLM-observability rows.
- `scripts/generate_ai_data.py`: generated 2,000 multimodal docs and 1,578 agent trace steps.
- `python -m pytest`: PASS, 24/24 tests.
- `scripts/run_all.py`: PASS, 8/8 notebooks.

## Key Results

- NB1: Delta log JSON commits are visible; schema enforcement blocks `age='thirty'`; `schema_mode='merge'` adds `tier`.
- NB2: 200 files before optimization, 55 after; speedup 4.7x and files-pruned ratio 55.0x.
- NB3: MERGE upserted 100,000 rows; RESTORE removed bad rows; history has 5 versions including RESTORE.
- NB4: Bronze 200,000 rows, Silver 190,052 rows; Gold has 24 rows across 7+ dates and 3 models.
- NB5: Iceberg pruning ratio meets target; field ID remains stable after rename; two partition specs coexist.
- NB6: Maintenance jobs pass: compaction, clustering, vacuum/expiry, orphan sweep, checkpoint.
- NB7: Random-access amplification, int8 compression/recall/topic fidelity, SQL search, stale-index lifecycle bug and CDF deletes are demonstrated.
- NB8: Agent trajectory medallion, pinned replay, cached catalog surface, destructive-call confirmation, tasks, provenance buckets and erasure are demonstrated.
