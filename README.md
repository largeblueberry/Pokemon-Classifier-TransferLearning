# 🐾 포켓몬 이미지 분류 프로젝트 (Pokemon Classification)

이 프로젝트는 PyTorch와 전이 학습(Transfer Learning)을 활용하여 150종의 포켓몬 이미지를 분류하는 딥러닝 모델을 구축한 프로젝트입니다.

## 1. 실험 환경

- **Framework:** PyTorch
- **Hardware:** Google Colab (T4 GPU)
- **Dataset:** PokemonData (150 classes)

### 2. 실험 설계 및 결과

두 가지 사전 학습된 모델(Pre-trained Models)의 학습 과정을 비교 분석한 결과는 다음과 같습니다.

### **(1) 학습 및 검증 정확도 (Accuracy Comparison)**

- **빠른 초기 수렴:** 두 모델 모두 첫 번째 Epoch에서 정확도가 가파르게 상승하며 전이 학습의 효과를 뚜렷하게 보여주었습니다.
- **성능 역전:** 초기(Epoch 0)에는 MobileNetV2의 검증 정확도가 높게 시작했으나, 학습이 진행됨에 따라 **ResNet18이 MobileNetV2의 정확도를 추월**하며 더 높은 최종 성능을 기록했습니다.
- **일반화 성능:** MobileNetV2는 훈련 정확도와 검증 정확도 사이의 간격이 ResNet18보다 넓게 나타나 상대적으로 과적합(Overfitting)의 경향이 보인 반면, **ResNet18은 두 지표가 더 가깝게 유지되며 안정적인 일반화 성능**을 보였습니다.

### **(2) 손실값 변화 (Loss Comparison)**

- **일관된 감소:** 두 모델 모두 학습이 진행됨에 따라 손실값이 안정적으로 우하향하였습니다.
- **최적화 효율:** 학습 전 과정에서 **ResNet18의 손실값이 MobileNetV2보다 낮게 유지**되었으며, 이는 ResNet18이 본 데이터셋의 특징을 더 효과적으로 학습하고 있음을 시사합니다.

### 3. 결론

실험 결과, 본 포켓몬 데이터셋에서는 **ResNet18** 모델이 MobileNetV2보다 우수한 성능을 보였습니다.

- **최종 성능:** ResNet18이 MobileNetV2보다 더 높은 검증 정확도와 낮은 손실값을 달성하며 프로젝트의 최적 모델로 선정되었습니다.
- **종합 평가:** MobileNetV2는 경량 모델로서 빠른 학습이 가능했으나, 정확도와 안정성 측면에서는 ResNet18의 잔차 연결(Residual Connection) 구조가 150종의 다양한 포켓몬 이미지를 분류하는 데 더 적합한 것으로 판단됩니다.
