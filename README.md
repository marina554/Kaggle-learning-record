# Titanic TFDF Solution 🚢

## Overview

This project builds a survival prediction model for the Kaggle Titanic competition using TensorFlow Decision Forests (TFDF).

After comparing multiple machine learning approaches,  
TFDF with Gradient Boosted Trees achieved the best performance.

The final Public Leaderboard score was **0.79665**.

---

# Technologies Used

- Python
- pandas
- numpy
- TensorFlow
- TensorFlow Decision Forests (TFDF)

---

# Dataset

Kaggle Titanic Dataset

- train.csv
- test.csv

---

# Preprocessing

The following preprocessing steps were applied.

## Missing Value Handling

- Age → filled with median
- Fare → filled with median
- Embarked → filled with "S"

## Name Normalization

Special characters and punctuation were removed from passenger names.

Additionally, names were tokenized after converting the dataset into TensorFlow Dataset format.

---

# Ticket Features

The Ticket column was divided into:

- Ticket_number
- Ticket_item

Example:

```text
PC 17599
↓
Ticket_item = PC
Ticket_number = 17599
```

---

# Features Used

- Pclass
- Sex
- Age
- SibSp
- Parch
- Fare
- Embarked
- Cabin
- Ticket_number
- Ticket_item
- Name

---

# Model

## TensorFlow Decision Forests

Model used:

- GradientBoostedTreesModel

---

## Important Setting

### honest=True

This setting significantly improved generalization performance.

---

# Seed Averaging

Instead of using a single model,  
multiple models with different random seeds were trained and averaged.

- seed range(0, 20)

The prediction probabilities from each seed were averaged to create the final prediction.

---

# Threshold Tuning

Threshold values were adjusted for prediction probabilities.

The following thresholds achieved the best scores:

- 0.493
- 0.494
- 0.495

---

# Feature Engineering Experiments

## Effective Techniques

- Name tokenization
- Ticket decomposition
- Seed averaging
- Threshold tuning

## Less Effective Techniques

- Title extraction
- FamilySize
- IsAlone
- CabinLetter
- Manual correction

Some additional features caused overfitting or increased noise,
which reduced the Public LB score.

---

# Result

| Model | Public Score |
|---|---|
| TFDF + honest=True + seed averaging | 0.79665 |

---

# Discussion

This analysis showed that the following factors were important:

- Avoiding excessive feature engineering
- Stabilization through seed averaging
- Threshold tuning

TFDF demonstrated strong performance on categorical features
and worked particularly well for the Titanic dataset.

The experiments also showed that adding more features
does not always improve model accuracy.

---

# Future Improvements

- Cross-validation
- Ensemble methods
- Hyperparameter tuning with Optuna
- More advanced feature engineering

---

# Author

marina

ーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーーー

# Titanic TFDF Solution 🚢

## 概要

Kaggle Titanicコンペティションにおいて、
TensorFlow Decision Forests（TFDF）を用いた生存予測モデルを構築しました。

本分析では、複数の機械学習手法を比較した結果、
Gradient Boosted Trees を用いた TFDF が最も高い性能を示しました。

最終的に Public Leaderboard にて **0.79665** を達成しました。

---

# 使用技術

- Python
- pandas
- numpy
- TensorFlow
- TensorFlow Decision Forests (TFDF)

---

# 使用データ

Kaggle Titanic Dataset

- train.csv
- test.csv

---

# 前処理

以下の前処理を実施しました。

## 欠損値補完

- Age → 中央値補完
- Fare → 中央値補完
- Embarked → "S"

## Name 正規化

Name列に対して記号除去・整形を実施。

さらに TensorFlow Dataset 化後、
Name をトークン分割して学習に利用しました。

---

# Ticket特徴量

Ticket列を以下に分解。

- Ticket_number
- Ticket_item

例：

PC 17599
↓
Ticket_item = PC
Ticket_number = 17599

---

# 使用特徴量

- Pclass
- Sex
- Age
- SibSp
- Parch
- Fare
- Embarked
- Cabin
- Ticket_number
- Ticket_item
- Name

---

# モデル

## TensorFlow Decision Forests

使用モデル：

GradientBoostedTreesModel

---

## 重要設定

### honest=True

特に効果が大きかった設定。

honest=True を有効化することで、
汎化性能が向上した。

---

# seed averaging

単一モデルではなく、
複数seedの予測平均化を実施。

- seed range(0, 20)

各seedで学習した予測確率を平均し、
最終予測とした。

---

# threshold tuning

予測確率に対して threshold を調整。

特に以下が高スコアを示した。

- 0.493
- 0.494
- 0.495

---

# 試行した特徴量

## 有効だったもの

- Name tokenization
- Ticket分解
- seed averaging
- threshold tuning

## 効果が限定的だったもの

- Title抽出
- FamilySize
- IsAlone
- CabinLetter
- 手動補正

追加特徴量により過学習やノイズ増加が発生し、
Public LBスコアが低下するケースも確認された。

---

# 結果

| モデル | Public Score |
|---|---|
| TFDF + honest=True + seed averaging | 0.79665 |

---

# 考察

本分析では、

- 特徴量を増やしすぎない
- seed averaging による安定化
- threshold tuning

が重要であることを確認した。

特に TFDF はカテゴリ特徴量との相性が良く、
Titanicデータに対して高い性能を示した。

また、特徴量追加が必ずしも精度向上につながるわけではなく、
不要特徴量によるノイズ増加も確認された。

---

# 今後の改善案

- クロスバリデーション導入
- アンサンブル
- Optunaによるハイパーパラメータ探索
- より高度な特徴量エンジニアリング

---

# Author

marina
