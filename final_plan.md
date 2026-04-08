# Final Implementation Plan: From Completion to Victory

This plan consolidates V1, V2, and V3 into a single, prioritized list of steps to ensure we not only finish on time but also deliver a winning project. Each step is designed to be a clear, assignable task.

| Step | Priority | Task | Time Est. | Assign To |
|---|---|---|---|---|
| 1 | 🔴 P0 | **Fix Task 4 Baseline:** Debug `run_baseline.py` to ensure the Task 4 heuristic consistently scores 1.0. The issue is likely state persisting between episodes. | 20 min | Teammate 1 |
| 2 | 🔴 P0 | **Deploy to HuggingFace Spaces:** This is a critical gate for submission. | 30 min | Teammate 2 |
| 3 | 🟡 P1 | **Create Gymnasium Wrapper:** Implement `tool_chain_env_gym.py` to make the environment compatible with standard RL libraries. | 30 min | Teammate 1 |
| 4 | 🟡 P1 | **Add Pytest Suite:** Create a `tests/` directory with tests for reset isolation, grader bounds, and task-specific logic. | 30 min | Teammate 2 |
| 5 | 🟡 P1 | **Implement TRL Training Loop:** Create `train_with_trl.py` to demonstrate agent training. | 60 min | Teammate 1 |
| 6 | 🟡 P1 | **Add Seed for Reproducibility:** Add a `seed` parameter to the `reset()` function and API endpoint. | 15 min | Teammate 2 |
| 7 | 🟡 P1 | **Enhance `openenv.yaml`:** Add `health_endpoint`, `tags`, `reward_range`, `stochastic`, and `license`. | 10 min | Teammate 1 |
| 8 | 🟡 P1 | **Write Reward Shaping Notes:** Create `docs/reward_shaping_notes.md` to explain the reward function design. | 20 min | Teammate 2 |
| 9 | 🟢 P2 | **Implement Task 5 "The Dark API":** Add the new task, including mock API handlers and grader logic. | 45 min | Teammate 1 |
| 10 | 🟢 P2 | **Add Anti-Exploit Hardening:** Implement checks to prevent common exploits. | 25 min | Teammate 2 |
| 11 | 🟢 P2 | **Create Multi-Episode Evaluation Harness:** Build `eval_agent.py` for robust evaluation. | 20 min | Teammate 1 |
| 12 | 🟢 P2 | **Improve README:** Add the "Comparison to Prior Work" table and the powerful V3 narrative paragraphs. | 20 min | Teammate 2 |
| 13 | 🟢 P2 | **Add Richer `info` in Step Response:** Enhance the `info` dictionary returned by the `step` function. | 10 min | Teammate 1 |
| 14 | 🔵 P3 | **Run Model Benchmarks:** Use `inference.py` to run benchmarks and create the leaderboard table for the README. | 60 min | Teammate 2 |
| 15 | 🔵 P3 | **Add Documentation:** Create `docs/agent_learning_curve.md`, `CONTRIBUTING.md`, and a `LICENSE` file. | 25 min | Teammate 1 |
| 16 | 🔵 P3 | **Set Up CI/CD:** Create a GitHub Actions workflow (`.github/workflows/ci.yml`) for continuous integration. | 15 min | Teammate 2 |
