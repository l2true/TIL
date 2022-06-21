# AutoEncoder



## AE의 목적

- Manifold leraning을 통해 feature의 차원을 줄이는 것



### 1. Denoising autoencoder

autoencoder의 성능을 높이기 위해 원래 데이터에 가우시안 필터를 입혀 학습시키는 방식



### 2. Convolution autoencoder

dense 방식이 아닌, convolution 방식의 autoencoder

학습할 데이터가 이미지 데이터기 때문에 convolution 사용하는 방식도 있음. 



### 3.  VAE

- AE가 Encoder를 이용해 차원을 줄이는 것이 목적인 반면, VAE는 Decoder를 이용해 새로운 데이터를 생성하기 위한 모델

- 학습 데이터의 분포를 따르는 '새로운 데이터'를 만드는 AE기반 생성 모델

- 단계

  1. encoder <- input
  2. reparameterization trick (sampling): data의 평균과 분산을 학습
     - epsilon 변수: data의 분포를 저장하는 random변수

  3. decoder -> output
     - sampling을 토대로 새로운 데이터를 생성