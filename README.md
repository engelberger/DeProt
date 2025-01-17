# DeProt
Code for DeProt. A protein language model with quantizied structure and disentangled attention

## 1 Install

```shell
git clone https://github.com/ginnm/DeProt.git
cd DeProt
pip install -r requirements.txt
export PYTHONPATH=$PYTHONPATH:$(pwd)
```

## 2 Structure quantizer

![Structure quantizer](images/structure_quantizer.png)

```python
from deprot.structure.quantizer import PdbQuantizer
processor = PdbQuantizer(structure_vocab_size=2048) # can be 20, 128, 512, 1024, 2048, 4096
result = processor("example_data/p1.pdb", return_residue_seq=False)
```

Output:
```
[407, 998, 1841, 1421, 653, 450, 117, 822, ...]
```


## 3 DeProt models have been uploaded to huggingface 🤗 Transformers
```python
from transformers import AutoModelForMaskedLM, AutoTokenizer
model = AutoModelForMaskedLM.from_pretrianed("AI4Protein/DeProt-2048", trust_remote_code=True)
tokenizer = AutoTokenizer.from_pretrained("AI4Protein/DeProt-2048", trust_remote_code=True)
```

### 3.1 Available models
| **Model** | **Description** |
|:---:|:---:|
| AI4Protein/Deprot-20 | structure vocab size = 20 |
| AI4Protein/Deprot-128 | structure vocab size = 128 |
| AI4Protein/Deprot-512 | structure vocab size = 512 |
| AI4Protein/Deprot-1024 | structure vocab size = 1024 |
| AI4Protein/Deprot-2048 | structure vocab size = 2048 |
| AI4Protein/Deprot-4096 | structure vocab size = 4096 |
| AI4Protein/Deprot-2048-NO_AA2SS | Ablative  |
| AI4Protein/Deprot-2048-NO_SS2AA | Ablative  |
| AI4Protein/Deprot-2048-NO_AA2POS | Ablative  |
| AI4Protein/Deprot-2048-NO_POS2AA | Ablative  |

## 4 Zero-shot mutant effect prediction

### 4.1 Example notebook
[Zero-shot mutant effect prediction](zero_shot/score_mutant.ipynb)

### 4.2 Run ProteinGYM Benchmark

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

## 5 Representation
```

```

## 6 Transfer-Learning
```

```

## Citation

If you use DeProt in your research, please cite the following paper:

```
@article {Li2024.04.15.589672,
	author = {Mingchen Li and Yang Tan and Bozitao Zhong and Ziyi Zhou and Huiqun Yu and Xinzhu Ma and Wanli Ouyang and Liang Hong and Bingxin Zhou and Pan Tan},
	title = {DeProt: A protein language model with quantizied structure and disentangled attention},
	elocation-id = {2024.04.15.589672},
	year = {2024},
	doi = {10.1101/2024.04.15.589672},
	publisher = {Cold Spring Harbor Laboratory},
	URL = {https://www.biorxiv.org/content/early/2024/04/17/2024.04.15.589672},
	eprint = {https://www.biorxiv.org/content/early/2024/04/17/2024.04.15.589672.full.pdf},
	journal = {bioRxiv}
}
```
