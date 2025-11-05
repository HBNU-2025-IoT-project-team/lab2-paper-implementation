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


