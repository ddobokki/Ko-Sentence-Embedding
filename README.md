# Ko-Sentence-Embedding
Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks(https://arxiv.org/abs/1908.10084)
- 한국어 문장 임베딩 모델입니다. https://huggingface.co/ddobokki/klue-roberta-small-nli-sts 에 공개가 되어 있습니다.
- 학습 데이터
  - KorNLUDatasets + KLUE NLI + KLUE STS
    - NLI train: multinli.train.ko.tsv, xnli.dev.ko.tsv, snli_1.0_train.ko.tsv, klue-nli-v1.1_train.json, klue-nli-v1.1_dev.json
  - STS
    - STS train: sts-train.tsv, klue-sts-v1.1_train.json
    - STS dev: sts-dev.tsv, klue-sts-v1.1_dev.json
    - STS test: sts-test.tsv
- 학습 전략
  - klue/roberta-small(https://huggingface.co/klue/roberta-small) 을 이용해 NLI 데이터를 먼저 학습시켰습니다.(MultipleNegativesRankingLoss 사용)
    - 모델의 타겟이 STS dataset이라 NLI train, dev를 둘다 학습시켰습니다.
  - 이후 STS dataset을 학습시켰습니다.

## Performance
- Semantic Textual Similarity test set results <br>

| Model                  | Cosine Pearson | Cosine Spearman | Euclidean Pearson | Euclidean Spearman | Manhattan Pearson | Manhattan Spearman | Dot Pearson | Dot Spearman |
|------------------------|:----:|:----:|:----:|:----:|:----:|:----:|:----:|:----:|
| KoSRoBERTa<sup>small</sup>    | 84.27 | 84.17 | 83.33 | 83.65 | 83.34 | 83.65 | 82.10 | 81.38 |

# Reference

```
@misc{park2021klue,
      title={KLUE: Korean Language Understanding Evaluation},
      author={Sungjoon Park and Jihyung Moon and Sungdong Kim and Won Ik Cho and Jiyoon Han and Jangwon Park and Chisung Song and Junseong Kim and Yongsook Song and Taehwan Oh and Joohong Lee and Juhyun Oh and Sungwon Lyu and Younghoon Jeong and Inkwon Lee and Sangwoo Seo and Dongjun Lee and Hyunwoo Kim and Myeonghwa Lee and Seongbo Jang and Seungwon Do and Sunkyoung Kim and Kyungtae Lim and Jongwon Lee and Kyumin Park and Jamin Shin and Seonghyun Kim and Lucy Park and Alice Oh and Jungwoo Ha and Kyunghyun Cho},
      year={2021},
      eprint={2105.09680},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```
```bibtex
@article{ham2020kornli,
  title={KorNLI and KorSTS: New Benchmark Datasets for Korean Natural Language Understanding},
  author={Ham, Jiyeon and Choe, Yo Joong and Park, Kyubyong and Choi, Ilji and Soh, Hyungjoon},
  journal={arXiv preprint arXiv:2004.03289},
  year={2020}
}
```
```
@inproceedings{reimers-2019-sentence-bert,
    title = "Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks",
    author = "Reimers, Nils and Gurevych, Iryna",
    booktitle = "Proceedings of the 2019 Conference on Empirical Methods in Natural Language Processing",
    month = "11",
    year = "2019",
    publisher = "Association for Computational Linguistics",
    url = "https://arxiv.org/abs/1908.10084",
}
```
