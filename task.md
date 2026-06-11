+++
object_kind = "task"
title = "Tabbit Hackathon Competition Workflow"
task_id = "20260610-tabbit-ntu-workflow-hackathon"
stage = "workflow-v0.1.1"
terminal_state = ""
priority = "P0"
paused = false
blocked = false
blocker_kinds = []
active_phase_id = "phase-01-workflow-construction"
assignee_account_id = "primary-account"
primary_repo = "https://github.com/zerong7777-boop/competition-agent-workflow"
supporting_repos = ["E:\\codex-home"]
machine_ids = []
parent_task_id = ""
parent_plan_node_id = ""
success_criteria = [
  "A reusable competition workflow exists with L0-L3 stages, submission gates, and leaderboard feedback records.",
  "The workflow reuses local Agent Harness concepts without modifying upstream harness files.",
  "Templates are concrete enough for a future competition task to instantiate.",
  "The workflow supports expert users making fast, evidence-backed leaderboard decisions."
]
constraints = [
  "Do not modify E:\\codex-home harness source files.",
  "Do not run experiments during workflow construction.",
  "Do not optimize for the demo before the mature workflow exists.",
  "Keep the official workflow distinct from the later hackathon demo version."
]
unknowns = [
  "Which concrete competition will be used for the final demo cut-down.",
  "Whether Tabbit itself will be used in the presentation."
]
tags = ["tabbit", "hackathon", "competition", "agent-harness", "workflow"]
linked_task_ids = []
source_refs = [
  "E:\\codex-home\\docs\\workflow",
  "E:\\codex-home\\tasks\\_templates\\task",
  "E:\\rz\\课题\\毕设\\CODEX_CONVERSATION_TEMPLATES_ZH.md"
]
created_at = "2026-06-10T00:00:00+08:00"
updated_at = "2026-06-10T00:00:00+08:00"
+++
# Tabbit Hackathon Competition Workflow

## Goal

Construct a first-place-oriented competition workflow specialized from the local Agent Harness. The workflow should help an expert user and agent move from rules and validation anchoring to strong-method adaptation, problem-driven structural innovation, competition engineering, and submission feedback loops.

## Non-Goals

- Do not build an execution automation engine in this workflow pass.
- Do not run a real competition experiment yet.
- Do not build the hackathon demo cut-down yet.
- Do not modify upstream Agent Harness files.

## Success Criteria

- L0-L3 workflow is documented.
- Each major stage has an actionable template.
- Submission intent and leaderboard feedback are explicit gates.
- L2 requires problem definition and innovation cards before structural specs.
- The workflow can later be instantiated on UAVM, Kaggle, or a similar benchmark competition.


