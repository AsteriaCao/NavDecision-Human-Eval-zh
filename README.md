# NavDecision Human Eval Navtest

This directory is a GitHub Pages compatible static package for the navtest
human-eval questionnaire.

## Build

Run from the repository root with the project environment:

```bash
/mnt/volumes/base-vla-ali-sh-mix/mayongjia/base-vla-ali-sh-mix/code/world_action_model/env/pwm/bin/python \
  tools/build_navtest_human_eval.py \
  --qa-json result_mid/text/result/stage2_rule_navtest_qa_en_train.json \
  --gpt-jsonl /lpai/volumes/base-vla-ali-sh-mix/pengshaoyang/code/autolabeling/output/navism/report/navdecision_gpt_score.jsonl \
  --config configs/sft_navsim/navsim_train.yaml \
  --samples-per-action 20 \
  --out-dir docs/navsim_human_eval_navtest \
  --overwrite
```

The builder samples 20 cases from each action group:

- Straight: `Straight`, `Keep`, `Intersection Straight`
- Turn Left: `Turn Left`
- Turn Right: `Turn Right`
- Change Lane: `Change Lane Left`, `Change Lane Right`
- Stop: `Stop`, `Pull Over`

Only GPT records with `qa_category == "planning.decision"` are used.

## Preview

```bash
python -m http.server 18081 --bind 0.0.0.0 --directory docs/navsim_human_eval_navtest
```

Open:

```text
http://10.80.131.56:18081
```

## GitHub Pages

Commit this directory including generated `manifest.json`, `metadata.json`, and
`assets/`. In GitHub Pages settings, publish from the `docs/` folder. The URL
will be:

```text
https://<owner>.github.io/<repo>/navsim_human_eval_navtest/
```

Each annotator exports their own JSONL or CSV from the browser.
# NavDecision-Human-Eval
# NavDecision-Human-Eval
