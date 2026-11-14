# Results: 128 vLLM Inference Throughput & Latency

**Main goal:** Measure vLLM serving throughput and latency  
**Tools:** Start python -m vllm.entrypoints.openai.api_server on port 8000, then run scripts/benchmark_serving.py

Reference results measured by the maintainer on the system shown in each section (generator TEMPLATE_00_141 · recorded 2026-11-14). Your own runs write `results/RESULTS_ACTUAL.md` in the same format.

> Smoke runs use deliberately small sizes. They check that the workload installs and runs end to end; their numbers are not performance results. Baseline and extended are.

<!-- profile:smoke -->
## smoke

- **System:** 1× AMD Instinct MI300X VF (196288 MB) · INTEL(R) XEON(R) PLATINUM 8568Y+ · Ubuntu 24.04.5 LTS · kernel 6.8.0-147-generic · driver 7.1.9.31600000
- **Run:** 2026-11-14T11:41:45Z · status **PASS** (exit 0)
- **Time (mm:ss):** setup 03:33 · benchmark 00:07 · whole run 05:04
- **Source:** run 128_20261114_114145
- **Command:** `bash run_benchmark.sh --smoke --model-name mistralai/Mistral-7B-v0.3 --dtype bfloat16 --tensor-parallel-size 1 --gpu-memory-utilization 0.9 --input-len 64 --output-len 16 --max-num-seqs 2 --max-concurrency 2`

| # | Metric | Result |
|---|---|---|
| 1 | Output token throughput (output_token_throughput_tokens_sec) | 393.50538060791445 |
| 2 | Time To First Token, ms (ttft_p50_msec) | 10.205173999565886 |
| 3 | Time Per Output Token, ms (time_per_output_token_tpot_p50_msec) | 4.677810266669742 |
| 4 | Inter-token latency, ms (inter_token_latency_itl_p50_msec) | 4.689188999691396 |
| 5 | End-to-end request latency p50, ms (end_to_end_request_latency_msec) | 80.46619400010968 |
<!-- /profile:smoke -->
