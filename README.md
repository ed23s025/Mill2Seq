# Mill2Seq

A deep learning-based approach for Milling Operation Sequence Generation.

Mill2Seq converts a raw B-Rep CAD (STEP) file into an optimal, collision-free milling
operation sequence. It uses a GATv2 graph network to detect machining features, a
Transformer to predict tools/axes/precedence, and a deterministic DAG + TSP solver to
generate the final safe sequence.

Paper: *Mill2Seq - A deep learning-based approach for Milling Operation Sequence Generation*
(Computers & Graphics, 2026)

## Installation

```bash
git clone https://github.com/ed23s025/Mill2Seq.git
cd Mill2Seq
pip install -r requirements.txt
```

## Dataset

98,623 synthetic CAD parts (24 feature classes). Download script and format details in
`data/README.md`.

```bash
bash data/download.sh
```

## Usage

Train:
```bash
python scripts/train.py --config configs/default.yaml
```

Evaluate:
```bash
python scripts/evaluate.py --checkpoint checkpoints/mill2seq_baseline.pt
```

Run inference on a STEP file:
```bash
python scripts/infer_end_to_end.py --step_file examples/part.step --checkpoint checkpoints/mill2seq_baseline.pt
```

## Results

| Metric | Value |
|---|---|
| Feature extraction rate | 96.32% |
| Tool prediction Micro-F1 | 99.79% |
| Precedence Macro-F1 | 97.84% |
| Sequence Valid Efficiency Score | 93.79% |

## Citation

```bibtex
@article{mill2seq2026,
  title   = {Mill2Seq - A deep learning-based approach for Milling Operation Sequence Generation},
  author  = {Satyam Kumar Verma},
  journal = {Computers \& Graphics},
  year    = {2026}
}
```

## License

MIT
