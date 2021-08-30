# 제 4절 관계(Relationship)

## 1.관계의 개념

### 1) 관계의 정의

관계(Relationship)를 사전적으로 정의하면 상호 연관성이 있는 상태로 말할 수 있다. 이것을 데이터 모델에 대입하여 정의해 보면, "엔터티의 인스턴스 사이의 논리적인 연관성으로서 존재의 형태로서나 행위로서 서로에게 연관성이 부여된 상태" 라고 할 수 있다. 
관계는 엔터티와 엔터티 간 연관성을 표현하기 때문에 엔터티의 정의에 따라 영향을 받기도 하고, 속성 정의 및 관계 정의에 따라서도 다양하게 변할 수 있다.

<img src ="https://user-images.githubusercontent.com/56623911/131367319-097e855f-5ac6-4366-9d97-fe50c97beeda.png"  width="70%" height="60%">



### 2) 관계의 페어링

<img src ="https://user-images.githubusercontent.com/56623911/131367366-3ed52f89-2528-4fbd-9b95-2e8f45c77ad0.png" width="70%" height="60%">

- 관계는 엔터티 안에 인스턴스가 개별적으로 관계를 가지는 것(페어링)이고 이것의 집합을 관계로 표현함.
- 관계는 두 엔터티 사이에 두 개 이상의 관계 형성 가능(1:1 /  1:M / M:N)
- 엔터티는 인스턴스의 집합을 논리적으로 표현하였다면, 관계는 관계 페어링의 집합을 논리적으로 표현한 것

## 2. 관계의 분류

<img src ="https://user-images.githubusercontent.com/56623911/131367405-999c510e-7f98-40e2-8f1a-bfb3072e4917.png" width="70%" height="60%">

관계는 존재에 의한 관계, 행위에 의한 관계로 구분

## 3. 관계의 표기법

### 관계명(Membership) : 관계의 이름

<img src ="https://user-images.githubusercontent.com/56623911/131367522-15e6a202-0510-4ab4-8390-110c7dc79cbf.png" width="70%" height="60%">

### 관계차수(Cardinality) : 1:1, 1:M, M:N

1) 1:1(ONE TO ONE) 관계를 표시하는 방법

<img src ="https://user-images.githubusercontent.com/56623911/131367577-e77a2bea-c902-46de-bb3b-cd37ec1c3c40.png" width="70%" height="60%">

2) 1:M(ONE TO MANY) 관계를 표시하는 방법

<img src ="https://user-images.githubusercontent.com/56623911/131367613-c6ca7a44-8ac1-4e6e-b09d-bc0c40684d18.png" width="70%" height="60%">

3) M:M(MANY TO MANY) 관계를 표시하는방법

<img src ="https://user-images.githubusercontent.com/56623911/131367636-e18f4210-25fa-4abc-b05d-4d67bb19abcc.png" width="70%" height="60%">


### 관계선택사양(Optionality) : 필수관계, 선택관계

<img src ="https://user-images.githubusercontent.com/56623911/131367709-57f80d06-a3cd-44ba-855a-2c3fdfe21764.png" width="70%" height="60%">


## 4. 관계의 정의 및 읽는 방법

### 1) 관계 체크사항

두 개 엔터티 사이에서 관계를 정의할 때 다음 사항을 체크해 보도록 한다.

- 두 개의 엔터티 사이에 관심있는 연관규칙이 존재하는가?
- 두 개의 엔터티 사이에 정보의 조합이 발생되는가?
- 업무기술서, 장표에 관계연결에 대한 규칙이 서술되어 있는가?
- 업무기술서, 장표에 관계연결을 가능하게 하는 동사(Verb)가 있는가 ?

### 2) 관계 읽기

- 기준(Souce) 엔터티를 한 개(One) 또는 각(Each)으로 읽는다.
- 대상(Target) 엔터티의 관계참여도 즉 개수(하나, 하나 이상)를 읽는다.
- 관계선택사양과 관계명을 읽는다.
