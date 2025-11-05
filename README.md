# LAB 2: 논문 분석
### 본 레포지토리는 2025년 하반기 국립한밭대학교 강의 "사물인터넷"의 두 번째 프로젝트인 '논문 분석'을 위한 레포지토리입니다

- 해당 논문: [Exploring the Vulnerabilities of Federated Learning: A Deep Dive into Gradient Inversion Attacks](https://huggingface.co/papers/2503.11514)
- 저자:
  - [Pengxin Guo](https://huggingface.co/gpx333)
  - [Runxi Wang](https://huggingface.co/Rx-Wang)
  - [Shuang Zeng](https://huggingface.co/stevezs)
  - [Jinjing Zhu](https://huggingface.co/Jinjing08)
  - [Haoning Jiang](https://huggingface.co/haoning666)
  - [Yanran Wang](https://huggingface.co/yanranw1)
  - [Yuyin Zhou](https://huggingface.co/RitaCoding)
  - [Feifei Wang](https://huggingface.co/feifeiwang)
  - Hui Xiong
  - [Liangqiong Qu](https://huggingface.co/Liangqiong-QU)
- 발행일: 2025.03.13
- 초록
  - 연합학습(FL)은 원본 데이터를 공유하지 않고 협력적으로 모델을 훈련하는 유망한 프라이버시 보호 패러다임으로 부상했습니다. 그러나 최근 연구에 따르면 공유된 그래디언트 정보를 통해 개인 정보가 여전히 유출될 수 있으며, 그래디언트 역전 공격(GIA)에 의해 공격받을 수 있습니다. 많은 GIA 방법이 제안되었지만, 이러한 방법에 대한 상세한 분석, 평가 및 요약은 여전히 부족합니다. 다양한 설문 논문이 FL의 기존 프라이버시 공격을 요약하고 있지만, GIA의 효과와 관련 제한 요소를 밝히기 위해 광범위한 실험을 수행한 연구는 거의 없습니다.

  - 이러한 격차를 메우기 위해, 우리는 먼저 GIA에 대한 체계적인 검토를 수행하고 기존 방법들을 최적화 기반 GIA(OP-GIA), 생성 기반 GIA(GEN-GIA), **분석 기반 GIA(ANA-GIA)**의 세 가지 유형으로 분류합니다. 그런 다음, FL에서 세 가지 유형의 GIA를 포괄적으로 분석 및 평가하여 성능, 실용성 및 잠재적 위협에 영향을 미치는 요인에 대한 통찰력을 제공합니다.

  - 우리의 연구 결과에 따르면, OP-GIA는 만족스럽지 못한 성능에도 불구하고 가장 실용적인 공격 설정인 반면, GEN-GIA는 많은 의존성을 가지고 있고 ANA-GIA는 쉽게 탐지되어 둘 다 비현실적입니다. 마지막으로, 우리는 더 나은 프라이버시 보호를 위해 FL 프레임워크 및 프로토콜을 설계할 때 사용자에게 3단계 방어 파이프라인을 제공하고, 우리가 추구해야 한다고 생각하는 공격자 및 방어자 관점에서의 향후 연구 방향을 공유합니다.

  - 우리는 이 연구가 연구자들이 이러한 공격에 방어하기 위해 더 강력한 FL 프레임워크를 설계하는 데 도움이 되기를 바랍니다.
- 코드 구현체: <img width="16" height="16" alt="image" src="https://github.com/user-attachments/assets/4ad11ba6-b2b0-42c0-80e0-27d66a679824" />
[Github](https://github.com/1wrx1/GIA)
---

# Exploring the Vulnerabilities of Federated Learning: A Deep Dive into Gradient Inversion Attacks

**[Exploring the Vulnerabilities of Federated Learning:
A Deep Dive into Gradient Inversion Attacks](https://pengxin-guo.github.io/FLPrivacy/)** \
[Pengxin Guo](https://pengxin-guo.github.io/)\*, [Runxi Wang](https://scholar.google.com/citations?user=wClrSiMAAAAJ&hl=zh-CN)\*, Shuang Zeng, Jinjing Zhu, Haoning Jiang, Yanran Wang, Yuyin Zhou, Feifei Wang, Hui Xiong, and [Liangqiong Qu](https://liangqiong.github.io/)

## 사용법

### 1. 준비 단계

#### 1.1 레포지토리 복제

```bash
git clone https://github.com/1wrx1/GIA.git
cd GIA
```

#### 1.2 환경 설치

```bash
conda env create -f environment.yml 
conda activate GIA 
```

### 2. 평가
#### 2.1 OP-GIA
##### 2.1.1 IG
- 예시: ImageNet 데이터셋에서 훈련되지 않은 모델을 사용하여 배치 크기 64로 IG의 공격 성능을 평가합니다.

```bash
cd OP-GIA/IG
python -u inverting.py --dataset ImageNet --num_classes 1000 --img_shape 224 --batch_size 64 --gpu 0 --root $root
```
- `$root`를 ImageNet의 루트 경로로 설정하세요.

- 더 많은 명령어는 `run.sh`파일에 제공됩니다.

#### 2.2 GEN-GIA
##### 2.2.1 GGL

```bash
cd GEN-GIA/GGL
```
- ImageNet 데이터셋에서 GGL을 실행하는 노트북 예제는 `ImageNet-ng-My-All-Images.ipynb`에 제공됩니다.

- 실용적인 시나리오 하에 ImageNet 데이터셋에서 GGL을 실행하는 노트북 예제는 `ImageNet-ng-My-All-Images-FedAvg.ipynb`에 제공됩니다.

- CIFAR-100 데이터셋에서 GGL을 실행하는 노트북 예제는 `CIFAR-100-ng-My-All-Images.ipynb`에 제공됩니다.

##### 2.2.2 CI-Net

- 예시: ImageNet 데이터셋에서 sigmoid 활성화 레이어를 사용하는 ResNet18 모델을 대상으로, 배치 크기 64로 CI-Net의 공격 성능을 평가합니다.

```bash
cd GEN-GIA/CI-Net
python -u main.py --dataset imagenet --root $root --arch resnet18 --bs 64 --act sigmoid
```
- `$root`를 ImageNet의 루트 경로로 설정하세요.

- 더 많은 명령어는 `run.sh`파일에 제공됩니다.

##### 2.2.3 LTI

- 예시: CIFAR10 데이터셋에서 LeNet 모델을 대상으로, 배치 크기 1로 LTI의 공격 성능을 평가합니다.

```bash
cd GEN-GIA/LTI
python -u main_learn_dlg.py --lr 1e-4 --epochs 200 --leak_mode None --model MLP-3000 --dataset CIFAR10 --batch_size 256 --shared_model LeNet --data_root $data_root --checkpoint_root $checkpoint_root
```
- `$data_root`는 CIFAR10의 루트 경로로, `$checkpoint_root`는 체크포인트를 저장할 루트 경로로 설정하세요.

- 결과를 평가하기 위한 노트북은 `Results--Vision.ipynb`에 제공됩니다.

- 더 많은 명령어는 `run.sh` 파일에 제공됩니다.

#### 2.3 ANA-GIA
##### 2.3.1 Robbing the Fed

```bash
cd ANA-GIA/RoF
```
- 노트북 예제는 `breaching_fl-My-All-Images.ipynb`에 제공됩니다.

##### 2.3.2 Fishing

- 예시: ImageNet 데이터셋에서 ResNet18 모델을 대상으로, 배치 크기 64로 Fishing의 공격 성능을 평가합니다.

```bash
cd ANA-GIA/fish
python -u fish.py --bs 64 --resolution 224 --arch resnet18 --root $root
```
- `$root`를 ImageNet의 루트 경로로 설정하세요.

- 더 많은 명령어는 `run.sh` 파일에 제공됩니다.

## 감사의 말
- 코드를 공개해 주신 다음 저자분들께 감사드립니다: [IG](https://github.com/JonasGeiping/invertinggradients), [GGL](https://github.com/zhuohangli/GGL), [CI-Net](https://github.com/czhang024/CI-Net), [LTI](https://github.com/wrh14/Learning_to_Invert), [Robbing the Fed](https://github.com/lhfowl/robbing_the_fed), [Fishing](https://github.com/JonasGeiping/breaching).


