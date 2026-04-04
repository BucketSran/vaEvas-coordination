# meta.json Minimal Template (raw / verified)

Use this template when converting an example into a benchmark seed.

For a new case, start with:

1. `tier = raw`
2. `verification_status = pending`

Promote to `verified` only after passing the required validation gate.

---

```json
{
  "task_id": "[TODO]",
  "task_name": "[TODO]",
  "category": "[TODO]",
  "source": {
    "type": "example",
    "path": "[TODO]"
  },
  "tier": "raw",
  "verification_status": "pending",
  "owner": "[TODO]",
  "created_at": "2026-04-04",
  "checks": {
    "dut_compile": "required",
    "tb_compile": "required",
    "tran_generated": "required",
    "sim_correct": "required",
    "parity_required": false
  },
  "evidence": {
    "result_path": "[TODO]",
    "pr_link": "[TODO]",
    "notes": "[TODO]"
  }
}
```

---

## Promotion Example

When promoted to verified:

```json
{
  "tier": "verified",
  "verification_status": "passed",
  "checks": {
    "parity_required": true
  },
  "evidence": {
    "result_path": "[updated result path]",
    "notes": "EVAS and Spectre parity gate passed."
  }
}
```
