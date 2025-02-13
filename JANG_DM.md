# Kfold
## [`sklearn.model_selection`]

###  가장 보편적으로 사용되는 교차 검증 기법

###  먼저 K개의 데이터 폴드 세트를 만들어서 K번만큼 각 폴드 세트에 학습고 검증 평가를 1반복적으로 수행하는 방법
 ### - 파라미터 
 * **n_splits**(int, default=5)
 -- 디폴트값 5
 --   n_splits 는 데이터 분할 수
 
* **shuffle**bool, default=False
-- shuffle은  매번 데이터를 분할하기전 섞을지 말지 여부를 선택합니다.

* **random_state**int, RandomState instance or None, default=None
-- scikit learn에서 사용하는 random_state 인자는 수행 시마다 동일한 결과를 얻기 위해 적용합니다.


# StratifiedFold
##  [`sklearn.model_selection`]

###  불균형한 분포도를 가진 레이블 데이터 집합을 위한 KFold 방식입니다.

###  먼저 K개의 데이터 폴드 세트를 만들어서 K번만큼 각 폴드 세트에 학습/검증 평가를 반복적으로 수행하는 방법(레이블 데이터가 왜곡됐을 경우 반드시)
### - 파라미터 
* **n_splits**int, default=5
-- 접기 수 2 이상이어야합니다.

* **shuffle**bool, default=False
-- 배치로 분할하기 전에 각 클래스의 샘플을 섞을 지 여부입니다. 각 분할 내의 샘플은 섞이지 않습니다.

* **random_state**int, RandomState instance or None, default=None
-- scikit learn에서 사용하는 random_state 인자는 수행 시마다 동일한 결과를 얻기 위해 적용합니다.



# CROSS_VAL_SCORE

## [`sklearn.model_selection.cross_val_score`]
#####  예시 ) scores = cross_val_score(estimator=df_clf, X=data, y=target, scoring="accuracy", cv=3)  
  

### 교차 검증을 보다 간편하게 실행할 수 있다 

###  내부에서 Estimator를  학습, 예측, 평가까지 시켜주므로 간단하게 교차 검증을 수행할 수 있습니다.

### - 파라미터 
 * **estimator**
 -- 평가자 , 데이터
 * **X**
-- feature 데이터 세트 , 대문자로 사용해야 함
 * **y**
 -- target 데이터(레이블)
 * **scoring**
 -- 예측 성능 검사 지표
  * **cv**
  -- 교차 검증 폴드 수




# StandardScaler

## [`sklearn.preprocessing.StandardScaler`]
#####  예시 )scaler =  StandardScaler() (메소드체이닝(chaining)을 사용하여 fit과 transform을 연달아 호출합니다)
##### X_scaled = scaler.fit(X_train).transform(X_train)


###  사이킷런에서 제공하는 표준화를 위한 클래스이며, 개별 변수를 평균이 0이고 분산이 1인 가우시안 정규 분포를 가질 수 있도록 값을 변환해준다

## 사용법 -메소드 중요
1.  데이터셋을 불러온다.
2.  StandardScaler를 선언하여 StandardScaler() 메소드를 사용한다.
3.  **fit()** 메소드로 데이터 분포가 정규분포를 만족하도록 모델을 **학습**시킨다.
4.  **transform()** 메소드로 정규 분포에 따르는 데이터 값을 **ndarray** 형식으로 받는다.
5.  반환 받은 ndarray 데이터를 pandas의 DataFrame() 메소드를 사용하여 DataFrame 형식으로 변환한다.





# MinMaxScaler
## [`sklearn.preprocessing.StandardScaler`]
**예시)scaler=MinMaxScaler()**
		**scaler.fit(iris_df))**
		**iris_scaled=scaler.transform(iris_df)**


###   Sklrean(사이킷런)에서 제공하는 정규화를 위한 클래스이며, 데이터 값을 0과 1 사이의 범위 값으로 변환한다. 음수 값이 있으면 -1에서 1 사이의 범위 값으로 변환한다.

## 사용법 -메소드 중요
1.  데이터셋을 불러온다.
2.  MinMaxScaler를 선언하여 MinMaxScaler() 메소드를 사용한다.
3.  ** fit()** 메소드로 데이터 범위가 [0, 1]이 되도록 최솟값은 0, 최댓값은 1을 갖도록 모델을 학습시킨다.
4.  **transform()** 메소드로 [0, 1] 범위에 따르도록 데이터 값을 ndarray 형식으로 받는다.
5.  반환 받은 ndarray 데이터를 pandas의 DataFrame() 메소드를 사용하여 DataFrame 형식으로 변환한다.


# DecisionTreeClassifier

## [`sklearn.tree.DecisionTreeClassifier`]
#####  예시 )DecisionTreeClassifier(random_state=156)
#### DecisionTreeClassifier(criterion, splitter, max_depth, min_samples_split, min_samples_leaf, min_weight_fraction_leaf, max_features, random_state, max_leaf_nodes, min_impurity_decrease, min_impurity_split, class_weight, presort)


### 분할과 가지치기 과정을 반복하면서 모델을 생성한다
###  결정트리에는 분류와 회귀 모두에 사용할 수 있다

### - 파라미터 
* **criterion**(default : gini)
 -- 분할 품질을 측정하는 기능
 * **splitter**(default:best)
-- 각 노드에서 분할을 선택하는 데 사용되는 전략
 * **max_depth**
 -- 트리의 최대 깊이(값이 클수록 모델의 복잡도가 올라간다.
 * **min_samples_split**(default:2)
 -- 자식 노드를 분할하는데 필요한 최소 샘플 수
 * **min_samples_leaf**(default:1)
 -- 리프 노드에 있어야 할 최소 샘플 수 
  * **min_weight_fraction_leaf**
 -- min_sample_leaf와 같지만 가중치가 부여된 샘플 수에서의 비율
  * **max_features**
 -- 각 노드에서 분할에 사용할 특징의 최대 수
* **random_state**
* **max_leaf_nodes**
 -- 리프 노드의 최대 수
* **min_impurity_decrease**
 -- 최소 불순도
 * **min_impurity_split**
 -- 나무 성장을 멈추기 위한 임계치
  * **class_weight**
 -- 클래스 가중치
   * **presor**
 -- 데이터 정렬 필요 여부
 

# Gridsearch

## [`sklearn.model_selection.GridSearchCV`]
#####  예시 )GridSearchCV(model, param_grid, cv=5, return_train_score=True)

###  기존엔 단순히 학습 데이터 세트와 테스트 데이터 세트로 데이터를 나눴다.
### 만약 매개변수를 조정하기 위해 테스트 세트를 사용하면 추후 모델 평가에 테스트 세트를 더 이상 사용할 수 없다.
### 즉, 평가를 위해 모델을 만들 때 사용하지 않은 독립된 데이터셋이 필요하다.
### 데이터를 세 개의 세트로 나눠 이 문제를 해결
### 학습 데이터 세트 : 모델을 작성
### 검증 데이터 세트 : 모델의 매개변수 선택
### 테스트 데이터 세트 : 모델의 성능 평가
#### -    GridSearchCV 객체에서 fit() 매소드를 시행하면 최적의 매개변수를 찾아줄 뿐만 아니라 교차 검증 성능이 가장 좋은 매개변수로 전체 훈련 데이터 세트에 대해 새로운 모델을 자동을 만든다.
#### - GridSearchCV는 이러한 전체 데이터로 학습한 모델에 접근할 수 있도록 predict()와 score() 메소드를 제공한다.



### - 파라미터 
 * **pram_grid**(매개변수 그리드)
 --  사용자가 관심있는 매개변수 전체를 대상으로 가능한 모든 조합을 시도해보는 것이다.
 * **cv**
 --  교차검증 분할 수
  * **return_train_score**
 --  train_score 리턴여부


# Randomforest

## [`sklearn.ensemble.RandomForestClassifier`]
#####  예시) RandomForestClassifier(n_estimators, criterion, max_depth, min_samples_split, min_samples_leaf, min_weight_fraction_leaf, max_features, max_leaf_nodes, min_impurity_decrease, min_impurity_split, bootstrap, oob_score, n_jobs, random_state, verbose, warm_start, class_weight)
**예시)model = RandomForestClassifier(n_estimators=5, random_state=0)**
		**model.fit(X_train, y_train)**

-   기본 결정트리는 해당 데이터에 대해 맞춰서 분류를 진행한 것이기 때문에 과적합 현상이 자주 나타났다.
-   그에 따라 이를 개선하기 위해 2001년 앙상블 기법으로 고안된 것이 랜덤 포레스트이다.
-   훈련 과정에서 구성한 다수의 결정 트리들을 랜덤하게 학습시켜 분류 또는 회귀의 결과도출에 사용된다.
-   즉, 특정 특성을 선택하는 트리를 여러개 생성하여 이들을 기반으로 작업을 수행하는 것이다.
-   각각의 트리가 독립적으로 학습하기 때문에 학습과정을 병렬화할 수 있다.
-   일반적인 의사결정트리는 Tree Correlation이라고 하는 특정 feature 하나가 정답에 많은 영향을 주게되면 대부분의 결과치가 유사하게 나타나는 문제점이 있었다.
-   하지만 랜덤 포레스트에서는 그러한 문제를 해결했고, 파라미터의 개수가 적어 튜닝도 쉽다.
-   타깃 예측을 잘하며 각각이 구별되는 여러개의 트리를 만들기 위해 무작위성이 부여된다.
-   대표적인 '배깅' 모델이다. (cf. 배깅(Bagging)은 bootstrap aggregating의 줄임말이다.)
-   결정트리의 단점을 보완하고 장점은 그대로 가지고 있는 모델이어서 별다른 조정 없이도 괜찮을 결과를 만들어낸다.
-   랜덤하게 만들어지기 때문에 random_state를 고정해야 같은 결과를 볼 수 있다.
-   트리 개수가 많아질 수록 시간이 더 오래 걸린다.
- 

## 사용법 -메소드 중요
1. 데이터를 받고 이를 학습데이터와 테스트데이터로 분류한다.
2.  모델을 생성하고 위의 학습데이터를 학습(fit)시킨다.
3.  이렇게 학습 후 생성된 랜덤포레스트 내부 트리는 estimator_ 속성에 저장되어 있다.


#  LinearReression

## [`sklearn.linear_model.LinearRegression`]
#####  예시) LinearRegression(fit_intercept, normalize, copy_X, n_jobs)

###  linear regression은 RSS값을 최소로 만드는 w값을 찾는 과정인 것이다.

### - 파라미터 
* **it_intercept**(default : True)
 -- 모형에 상수항 (절편)이 있는가 없는 가를 결정하는 인수
 * **normalize**
-- 매개변수 무시 여부
 * **copy_X**
-- X의 복사 여부
 * **n_jobs**
-- 계산에 사용할 작업 수


#  Confusion_matrix

## [`sklearn.metrics.confusion_matrix`]
#####  예시) confusion_matrix(y_true, y_pred)


### - 파라미터 
* **y_true**(default : True)
 -- 정답
 * **y_pred**
-- 예측 결과

##  결과 예시)
-- **오차행렬:**
**[[402 1]**
**[ 6 41]]**
-   TN : 402 / FP : 1 / FN : 6 / TP : 41


# boosting에 대해서
-   하나의 앙상블에 포함된 여러 개의 분류기가 순차적으로 학습을 수행하되, 앞에서 학습한 분류기가 예측이 틀린 데이터에 대해서 올바르게 예측할 수 있도록 다음 분류기에게 가중치(weight)를 부여하면서 학습과 예측을 진행
-   주로 분류기에 약한 학습기를 사용 (약한 학습기 : 예측 성능이 상대적으로 떨어지는 학습 알고리즘, 대표적으로 결정트리)



# GradientBoostingClassifier

## [`sklearn.ensemble.GradientBoostingClassifier`]
#####  예시) model = GradientBoostingClassifier(random_state=42)
#####  model.fit(X_train, y_train)

-   여러 개의 결정 트리를 묶어 부스팅하는 앙상블 기법
-   회귀와 분류 모두에 사용 가능
-   랜덤하게 트리를 생성한 랜덤 포레스트와는 달리 그래디언트 부스팅은 이전 트리의 오차를 보완하는 방식으로 순차적으로 트리를 만듬 (무작위성이 없음)
-   보통 다섯 개 이하 깊이의 트리를 사용하므로 메모리를 적게 사용하고 예측도 빠르다.
-   각각의 트리는 데이터의 일부에 대해서만 맞춰져있어 트리가 많이 추가될수록 성능이 좋아짐
-   단점 : 매개변수를 잘 조정해야하며, 훈련시간이 길다. 트리의 특성상 고차원 희소 데이터에 대해서는 정상적 작동이 어렵다.
-   learning_rate : 이전 트리의 오차를 얼마나 강하게 보정할 것인지를 제어 (학습률이 크면 트리는 보정을 강하게 하기 때문에 복잡한 모델을 만듬)
-   n_estimators 값을 키우면 앙상블에 트리가 더 많이 추가되어 모델의 복잡도가 커지고 훈련 세트에서의 오차를 더 잘 바로잡을 수 있음


### - 파라미터 
* **n_estimators**
 -- 생성할 트리의 개수 (트리가 많아질 수록 과대적합 가능성 증가)
 * **learning_rate**
 -- 오차를 보정하는 정도 (값이 높을 수록 오차를 많이 보정하려고 함 )
 * **max_depth**(default : True)
 -- 트리의 최대 깊이 (일반적으로 트리의 깊이를 깊게 설정하지 않음)
 


#  SVM(서포트벡터머신)
## [`sklearn.svm.SVC`]

#####  예시) 
from sklearn.svm import SVC

classifier = SVC(kernel = 'linear')

training_points = [[1, 2], [1, 5], [2, 2], [7, 5], [9, 4], [8, 2]]

labels = [1, 1, 1, 0, 0, 0]

classifier.fit(training_points, labels)

--------------------------------------------------------------------------------------

- SVM은 분류에 사용되는 지도학습 머신러닝 모델이다.
-   SVM은 서포트 벡터(support vectors)를 사용해서 결정 경계(Decision Boundary)를 정의하고, 분류되지 않은 점을 해당 결정 경계와 비교해서 분류하게 된다.
-   기존의 퍼셉트론은 가장 단순하고 빠른 분류 모형이지만 결정경계가 유일하게 존재하지 않는다.
-   서포트 벡터 머신(SVM)은 퍼셉트론 기반의 모형에 가장 안정적인 결정 경계를 찾기 위해 제한 조건을 추가한 모형이라고 볼 수 있다.
-   서포트 벡터 : 클래스 사이 경계에 가깝게 위치한 데이터 포인트 (결정 경계와 이들 사이의 거리가 SVC 모델의 dual_coef_에 저장된다.)



### - 파라미터 
* **Kernel**
 -- 생성할 트리의 개수 (트리가 많아질 수록 과대적합 가능성 증가)
 --원래 가지고 있는 데이터를 더 높은 차원의 데이터로 변환한다. 2차원의 점으로 나타낼 수 있는 데이터를 ****다항식**(polynomial) 커널**은 3차원으로, **RBF 커널**은 점을 무한한 차원으로 변환한다.
 * **C**
 --   C 매개변수는 각 포인트의 중요도(정확히는 dualcoef 값)를 제한하는 매개변수로, 해당값이 커질수록 결정경계가 데이터에 정확하게 맞춰진다.
 --**C 값이 클수록** 오류를 덜 허용하며 이를 **하드 마진(hard margin)**이라 부른다. 반대로 C 값이 작을수록 오류를 더 많이 허용해서 **소프트 마진(soft margin)**을 만든다.
 * **Gamma(γ)**
 -- 트리의 최대 깊이 (일반적으로 트리의 깊이를 깊게 설정하지 않음)
--**Gamma가 크면 decision boundary는 더 굴곡지고, Gamma가 작으면 decision boundary는 직선에 가깝습니다.**




#  XGBoost
## [`xgboost`](따로 설치해야함)
model = XGBClassifier()  
model.fit(X=iris_train[col_x], y=iris_train[col_y])  
model

- 앙상블 모델의 한 종류인 boosting의 종류이다. 부스팅은 약한 분류기를 세트로 묶어서 정확도를 예측하는 기법이다. 또한 Xgboosting은 gradient boosting 알고리즘의 단점을 보안해주기 위해 나왔다(느리고 과적합이라는 단점)




### - 파라미터 
* **objective**
 -- "binary:logistic“, “reg:linear”“, “multi:softmax” : 이항 / 연속 / 다항
* **max_depth**
 -- tree 구조가 간단한 경우 : 2
 * **nthread**
 -- cpu 사용 수 
  * **nrounds**
 -- 실제값과 예측값의 차이를 줄이기 위한 반복학습 횟수
   * **eta**(Default: 0.3)
 -- 학습률을 제어하는 변수, 오버 피팅을 방지



# KNeighborsClassifier
## [`sklearn.neighbors.KNeighborsClassifier`]
#####  예시) KNeighborsClassifier(n_neighbors, weights, algorithm, leaf_size, p, metric, metric_params, n_jobs)
classifier = KNeighborsClassifier(n_neighbors = 3)
training_points = [
[0.5, 0.2, 0.1],
[0.9, 0.7, 0.3],
[0.4, 0.5, 0.7]
]
training_labels = [0, 1, 1]
classifier.fit(training_points, training_labels)


### - 파라미터 
* **n_neighbors**(default : 5)
 -- 이웃의 수
* **weights**
 -- 예측에 사용된 가중 함수 (uniform, distance) (default : uniform / uniform : 가중치를 동등하게 설정, distance : 가중치를 거리에 반비례하도록 설정)
 * **algorithm**(auto, ball_tree, kd_tree, brute)
 -- 가까운 이웃을 계산하는데 사용되는 알고리즘
  * **leaf_size**
 -- BallTree 또는 KDTree에 전달 된 리프 크기
   * **p**
 -- (1 : minkowski_distance, 2: manhattan_distance 및 euclidean_distance)
   * **metric**
 -- 트리에 사용하는 거리 메트릭스
   * ** metric_params**
 --  메트릭 함수에 대한 추가 키워드 인수
   * ** n_jobs**
 -- 이웃 검색을 위해 실행할 병렬 작업 수



# VotingClassifier
## [`sklearn.ensemble.VotingClassifier`]
-   하드 보팅 : 최종 아웃풋 결과 중 각 모델들이 가장많이 선택한 아웃풋을 최종 아웃풋으로 설정한다.
-   소프트 보팅 : 최종 아웃풋 결과의 확률값을 기반으로 평균을 내어, 이중 가장 확률값이 높은 아웃풋을 최종 아웃풋으로 설정한다.
#### sklearn.ensemble.VotingClassifier(estimators, *, voting='hard', weights=None, n_jobs=None, flatten_transform=True, verbose=False)


## 사용법 -메소드 중요
1. 데이터셋을 불러와 훈련셋과 테스트셋으로 나누었다.
2.  -   사이킷런에서 모델들을 불러오고, Voting분류기 모델에 포함시켰다.
3.  -   보팅방식 선택했다.
4.   두 모델과 보팅 분류기 모델을 학습시키고(fit) 평가했다.



### - 파라미터 
* **estimators**
 --리스트 형식으로 튜플 형식의 앙상블 할 classifier를 넣어준다.
* **voting**(Default="hard")
 -- 보팅방법 선택





# Pipeline
## [`sklearn.pipeline.Pipeline`]
####Pipeline(_steps_, _*_, _memory=None_, _verbose=False_)

#### 파이프라인의 목적은 cross_validated 여러가지의 단계들을 합쳐 놓은 것이다. 그렇게 함으로써 파라미터 를 언더바 2개로 접근하여 수정이 가능하다. step변수들은 파라미터를 세팅해놓으면서, 대체가능 한마디로 여러가지 데이터 전처리를 하는 모델들을 한데 묶어서 또는 fit을 시키려고 하는 것. 

### - 파라미터 
* **verbose**
 --과정들을 계속  출력해줌







 