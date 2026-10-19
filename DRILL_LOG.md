# CI Drill Log

This pull request is the paper trail for an on-call rehearsal drill.

## What the drill is
Our runbook assumes every on-call engineer knows how to:
1. Cancel a stuck GitHub Actions job mid-flight
2. Re-run a cancelled workflow run from scratch

Nobody has actually practiced this on the account, so this repository is a
disposable playground for a full rehearsal.

## The setup
- Repository: `mcpmark-eval-liuhezi/ci-drill-2`
- Workflow: `.github/workflows/hold-and-release.yml` — a manual-dispatch
  (`workflow_dispatch`) workflow whose single job `hold` runs `sleep 300` on
  `ubuntu-latest`, giving a safe five-minute window to rehearse in.

## The drill steps
1. Trigger a manual run of `hold-and-release`, wait until the job is genuinely
   executing (past the queue), then cancel the run mid-flight and confirm the
   run ended with a `cancelled` conclusion.
2. Re-run the same cancelled run from scratch (a fresh attempt of the existing
   run, not a new dispatch), confirm the second attempt starts, then cancel it
   too so nothing keeps burning minutes.

## Outcome
See the PR comments for the recorded outcome of each stage.
