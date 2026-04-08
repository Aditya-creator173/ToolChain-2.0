# ToolChain-Env — Implementation Progress Tracker

Legend:
- [x] completed and verified
- [~] implemented, verification pending
- [ ] not started

Current validation note: the server startup and pytest checks are still failing, so code-heavy items should stay pending until those pass cleanly.

## Final Plan Checklist

### Step 1: Fix Task 4 Baseline (P0) | Difficulty: 7/10 | ETA to finish: 0 min (done)
- [x] Fix Task 4 baseline to consistently score 1.0.

### Step 2: Deploy to HuggingFace Spaces (P0) | Difficulty: 6/10 | ETA to finish: 35 min
- [ ] Deploy to HuggingFace Spaces.

### Step 3: Create Gymnasium Wrapper (P1) | Difficulty: 4/10 | ETA to finish: 20 min
- [~] Add Gymnasium wrapper (`tool_chain_env_gym.py`) — created, validation pending.

### Step 4: Add Pytest Suite (P1) | Difficulty: 5/10 | ETA to finish: 45 min
- [~] Add `tests/` with pytest coverage (files created; pytest run pending).

### Step 5: Implement TRL Training Loop (P1) | Difficulty: 8/10 | ETA to finish: 80 min
- [~] Add TRL training script scaffold (`train_with_trl.py`) — created, validation pending.

### Step 6: Add Seed for Reproducibility (P1) | Difficulty: 3/10 | ETA to finish: 20 min
- [~] Add seed parameter to reset flow (`/reset_task`, `/reset`, env reset).

### Step 7: Enhance `openenv.yaml` (P1) | Difficulty: 2/10 | ETA to finish: 0 min (done)
- [x] Add `health_endpoint` in `openenv.yaml`.
- [x] Add `reward_range`, `stochastic`, `tags`, `license` in `openenv.yaml`.

### Step 8: Write Reward Shaping Notes (P1) | Difficulty: 3/10 | ETA to finish: 0 min (done)
- [x] Add `docs/reward_shaping_notes.md`.

### Step 9: Implement Task 5 "The Dark API" (P2) | Difficulty: 9/10 | ETA to finish: 70 min
- [~] Add Task 5 "Dark API" in env/mock API/grader/spec/baseline.

### Step 10: Add Anti-Exploit Hardening (P2) | Difficulty: 7/10 | ETA to finish: 40 min
- [~] Add anti-exploit hardening:
	- [~] grader no-step gate + fingerprint
	- [~] token TTL enforcement
	- [~] idempotency-key replay guard

### Step 11: Create Multi-Episode Evaluation Harness (P2) | Difficulty: 5/10 | ETA to finish: 30 min
- [~] Add multi-episode eval harness (`eval_agent.py`).

### Step 12: Improve README (P2) | Difficulty: 2/10 | ETA to finish: 0 min (done)
- [x] Add "comparison to prior work" table in `README.md`.
- [x] Add V3 "nuclear" README paragraphs from plan.

### Step 13: Add Richer `info` in Step Response (P2) | Difficulty: 5/10 | ETA to finish: 25 min
- [~] Add richer `info` in step response (`partial_score`, task context, rate-limit remaining).

### Step 14: Run Model Benchmarks (P3) | Difficulty: 6/10 | ETA to finish: 95 min
- [ ] Add model leaderboard table in `README.md`.
- [ ] Run/record benchmark table across multiple models.

### Step 15: Add Documentation (P3) | Difficulty: 2/10 | ETA to finish: 0 min (done)
- [x] Add `docs/agent_learning_curve.md`.
- [x] Add `CONTRIBUTING.md`.
- [x] Add `LICENSE` file.

### Step 16: Set Up CI/CD (P3) | Difficulty: 4/10 | ETA to finish: 0 min (done)
- [x] Add CI workflow (`.github/workflows/ci.yml`).

## Pre-Submission Gates Verification
- [ ] HF Space deployed and checked at `/reset_task?task_id=task1`.
- [ ] `openenv validate` pass proof captured in repo.
- [ ] Docker build+run validation log captured.
- [x] Baseline produces non-error SCORE lines for all tasks.
- [x] `inference.py` emits required `[START]/[STEP]/[END]` format.
- [x] Graders return float score in [0.0, 1.0].

Open validation blockers:
- Server startup is still failing.
- Pytest is still failing.

## Bugs, Errors and Problems Faced, Might Face

### Currently facing (active blockers)
- Uvicorn startup failure: `uvicorn tool_chain_env.app:app --host 0.0.0.0 --port 8000` exits with code 1.
- Pytest failure: `python -m pytest --ignore=tool_chain_env/test_input.py` exits with code 1.
- Verification gap: several features are implemented but not fully re-validated after recent hardening/refactor changes.
- Integration uncertainty: edits in `app.py` and `server/tool_chain_env_environment.py` may have introduced behavior drift versus older tests/assumptions.

### Might face during further implementation
- Contract mismatches between API routes, payloads, and tests (especially if legacy tests target old endpoints).
- Grader regressions from anti-exploit logic (false negatives, stricter checks reducing previously passing flows).
- Task randomization side effects causing flaky baselines/tests if assumptions remain hardcoded in any script.
- Docker/runtime divergence where local virtualenv works but container build/run fails due to dependency or entrypoint differences.
- HuggingFace Space deployment issues (environment variables, startup command, network limits, cold-start delays).
- `openenv validate` failures if exposed routes/spec fields do not exactly match expected OpenENV conventions.
- Benchmark instability across models due to rate limits, token/context limits, or non-deterministic agent outputs.
