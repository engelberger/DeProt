# DeProt
Code for DeProt. A protein language model with quantizied structure and disentangled attention

## Structure quantizer

![Structure quantizer](images/structure_quantizer.png)

```python
from deprot.structure.quantizer import PdbQuantizer
processor = PdbQuantizer(structure_vocab_size=2048)
result = processor("example_data/p1.pdb", return_residue_seq=False)
```

Output:
```
[407, 998, 1841, 1421, 653, 450, 117, 822, ...]
```


## Using DeProt with huggingface transformers
```python
from transformers import AutoModelForMaskedLM
model = AutoModelForMaskedLM.from_pretrianed("AI4Protein/DeProt-2048")
```

## Zero-shot mutant effect prediction
See notebook [Zero-shot mutant effect prediction](zero_shot/score_mutant.ipynb)

### Run ProteinGYM Benchmark

Download dataset from [Google Driver](https://drive.google.com/file/d/1lSckfPlx7FhzK1FX7EtmmXUOrdiMRerY/view?usp=sharing).
(This file contains quantized structures within ProteinGYM).

```shell
cd example_data
unzip proteingym_benchmark.zip
```

```shell
python zero_shot/proteingym_benchmark.py --model_path AI4Protein/DeProt-2048 \
--structure_dir example_data/structure_sequence/2048
```

## Representation
```

```

## Transfer-Learning
```

```

## Citation

If you use DeProt in your research, please cite the following paper:

```

```