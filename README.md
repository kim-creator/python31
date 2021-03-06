K-NN(k-Nearest Neighbors, k-최근접 이웃) 알고리즘

k : 이웃의 개수 분류와 회귀 모두에 사용이 가능하며, 훈련된 데이터와 가장 가까운 k개의 데이터 포인트 찾기.

찾아낸 k 개의 데이터 포인트 중 가장 많은 ( 또는 가장 가까운 ) 데이터 포인트의 개수 (또는 거리)를 이용해 새로운 데이터 포인트를 분류 하거나 회귀합니다.

개수

거리

결정 경계 ( decision boundary )

클래스 0 또는 클래스 1로 분류 되어질 경계면 결정 경계라고 한다.

선형모델

딥러닝과 가장 가까운 알고리즘

선형대수의 연산과 관련이 크다.

가중치(w)와 편향(b)을 이용한 연산

y^=w1x1+w2x2+⋯+wnxn+b

W=⎡⎣⎢⎢⎢⎢⎢⎢w1w2w3...wn⎤⎦⎥⎥⎥⎥⎥⎥X=⎡⎣⎢⎢⎢⎢⎢⎢x1x2x3...xn⎤⎦⎥⎥⎥⎥⎥⎥

y^=WTX+b

아주 단순하게 보면( 특성이 한개인 경우 )

y^=w1x1+b

선형 회귀는 특성이 없으면 없을 수록 성능이 많이 떨어진다.

선형회귀 평가방법

MSE값이 최소화되는 W와 b값을 찾아낸다.

이 값들을 찾아내는 과정을 선형회귀의 학습이라고 한다.

이 때 사용되는 방법이 SVD(특이값 분해) 방식이다.

선형회귀 모델의 복잡도를 조절할 수 있는 모델

Ridge, Lasso 모델

규제 매개변수 (α)를 이용해 모델의 가중치에 패널티를 부여

α는 가중치를 억제하거나 증폭 시키는 역할을 한다.

라쏘(Lasso) 회귀

릿지와 마찬가지로 α 를 활용해서 가중치를 제어

릿지는 가중치를 0에 가깝게 만들 뿐, 0으로 만들지는 않는다.

라쏘는 실제 가중치를 0으로 만들어 버릴 수도 있다.( 특성 선택 ( feature selection ))

정리

일반적인 선형회귀 모델로써 LinearRegression을 사용한다.

Ridge, Lasso를 선택적으로 사용하게 되는데, Ridge는 모든 특성을 사용, Lasso는 일부 선택된 특성만 사용

일반적으로는 Ridge가 Lasso보다 선호된다.

선형 이진 분류( Linear Binary Classification )

y^=w1x1+w2x2+⋯+wnxn+b>0

선형 모델을 학습시키기 위한 알고리즘에 공통적으로 사용되는 기법

가중치(w)와 편향(b)의 조합이 훈련 데이터에 얼마나 잘 맞는지를 측정

사용할 수 있는 규제가 있는지...?(C)

C의 의미는 얼마나 오차를 허용하지 않을 것인가.

C가 커지면 커질 수록 오차를 없앤다. - 데이터를 중점적으로 보겠다. - 선형 모델에서는 w가 커진다.

C가 작아지면 작아질수록 오차를 허용 시키겠다. - 데이터의 추세를 보겠다. - 선형 모델에서는 w가 작아지기 시작한다.

각 알고리즘 마다 훈련 세트를 잘 학습시키는 방법이 모두 다르다. 잘못된 분류를 모두 수정하기 위한 모델 파라미터 조절은 수학적으로 불가능!

로지스틱 회귀 ( Logistic Regression ) - 이진 분류에서 logistic(sigmoid) 손실 사용, 다중 분류에서는 교차 엔트로피 손실함수 사용

서포트 벡터 머신( Support Vector Machine ) - 제곱 힌지 손실 함수 사용

선형 모드

비선형 모드

규제 매개변수 C

α (패널티): 회귀에서 사용된다.

α가 늘어나면 가중치를 낮춘다.

가중치의 크기와 반비례

C (규제) : 분류에서 사용된다.

C가 늘어나면 오차를 허용하지 않기위해 가중치를 늘린다.

가중치의 크기와 비례

즉 C가 커지면 모델은 데이터를 복잡하게 분석하기 시작 - 복잡도가 증가한다.

저차원 데이터 세트 같은 경우는 결정 경계가 직선 또는 평면 까지 밖에 활용 가능. - 제한적

선형 분류 모델은 특성의 개수가 많을 때 힘을 발휘 합니다.

두 세트의 점수가 모두 높아서 성능은 괜찮긴 하지만 점수가 비슷하다. - 과소적합 가능성이 있다!

선형 다중 분류

LogisticRegression을 이용한 다중 분류는 소프트맥스 함수를 사용

Pr(Yi=c)=eWc⋅Xi+b∑Kk=1eWk⋅Xi+b

정리

선형 모델의 주요 매개변수

alpha, C : 가중치에 연관된 하이퍼 파라미터

α : 값이 커지면 가중치가 낮아진다. 회귀에서 사용된다.

C : 값이 커지면 가중치가 높아진다. 분류에서 사용된다.

100, 10, 1, 0.1, 0.01 같은 로그 스케일로 설정하는 것이 보통이다.

장단점

장점

샘플(데이터의 양)에 비해서 특성이 많을 때 잘 작동한다.

다른 모델로 학습하기 어려운 매우 큰 데이터셋에도 선형 모델을 많이 사용한다. ( 예를 들어 딥러닝 )

딥러닝의 기반이 되는 알고리즘

다른 알고리즘 보다 속도가 빠르다.

단점

저차원 데이터 세트( 특성이 많이 없는 )에서는 일반화 성능이 좋지 않다.

Tree 계열 알고리즘

의사결정트리 (Decision Tree)

앙상블 모델

랜덤 포레스트( Random Forest )

그라디언트 부스팅 회귀 트리( Gradient Boosting Regressor Tree )

트리 알고리즘의 특징

데이터를 토대로 질문지를 만들어 낸다.

항상 이 질문은 YES / NO 로 결정 된다.

질문지를 만들어 내는 기준은 지니계수가 높은 것을 기준으로 만들어 낸다.

질문지는 노드( 리프 )로 구성되어 있다.

더 이상 질문을 할 수 없는 - 지니계수가 0인 노드를 순수 노드(pure node)라고 한다.

질문지의 깊이가 깊어지면 트리 모델의 복잡도가 올라간다.

기본적으로 의사결정 트리는 무조건 과대적합을 기본을 삼는다.

의사결정나무의 복잡도 제어

트리 생성을 일찍 중단( 사전 가지치기(pre pruning) ) - 사이킷런에서 사용하는 방식

트리를 다 만들고 데이터 포인트가 적은 노드를 삭제하거나 병합( 사후 가지치기(post pruning))

사전 가지치기 적용

max_depth 하이퍼 파라미터를 사용하여 사전에 최대 질문 깊이를 조절할 수 있다. -> 복잡도를 조절

트리의 특성 중요도 ( feature importance )

질문지를 만들기 위해 선택된 특성이 예측을 하기 위해 얼마나 중요한 특성인가

앙상블 모델 알아보기

랜덤 포레스트 ( Random Forest )

과대적합이 되어있는 트리를 여러개 준비한다.(n_estimators)

과대적합된 트리를 각각 다른 방향으로 예측을 하게 한다.

각각 다른 방향 : 무작위 특성을 활용해서 과대적합된 상태의 예측을 한다.

무작위 특성 : 무작위로 feature를 원본 데이터로부터 선택 - 부트스트랩 샘플링(Bootstrap Sampling)

부스트스랩 샘플링은 전체 데이터 특성(feature)에서 무작위로 의사결정트리를 위한 feature로 선정하는 방식

랜덤 포레스트의 주요 하이퍼 파라미터

n_estimators : 랜덤 포레스트에서 사용할 나무의 개수. 나무가 많아지면 복잡도가 증가

max_features : 부스트스랩 샘플링에 영향을 미친다. 나무에 사용할 샘플의 최대 개수(가짓수)

max_features가 원본 데이터 전체 특성과 같으면 무작성이 안들어 간다. 모든 나무가 똑같은 예측을 하게 된다.

max_features가 1이면 완전 무작위가 된다. 하나의 트리에 하나의 특성이 여러개 등록될 수도 있다.

그라디언트 부스팅 회귀 트리

학습이 약한 상태에서 강한 상태로 점점 바뀌어가는 알고리즘

랜덤 포레스트의 반대되는 개념

랜덤 포레스트는 과대적합된 트리를 활용

그라디언트 부스팅 회귀 트리는 과소적합된 트리를 활용

과소적합된 트리를 여러개 이어가면서 학습시키는 방법

gbrt는 복잡도를 조절하기 위한 중요한 하이퍼 파라미터

나무 개수(n_estimators)

나무의 질문 깊이(max_depth)

랜덤 포레스트의 장단점

장점

랜덤 포레스트는 머신러닝의 교과서라고도 할 수 있는 알고리즘

초보자도 굉장히 쉽게 이해할 수 있고, 사용할 수 있으며, 스케일링 등을 하지 않아도 웬만한 성능을 보장

데이터 분석 및 레포트 작성에도 굉장히 유리

딥러닝은 성능은 좋은데 데이터에 대한 해석이 어려워요

랜덤 포레스트는 성능은 딥러닝 보다는 뒤쳐지지만 데이터의 해석이 뛰어나요

딥러닝 모델 + 랜덤 포레스트 모델을 합친 방식의 모델도 사용

단점

트리를 여러개 훈련을 시켜서 평균을 내기 때문에 트리가 많아지면 훈련시간이 굉장히 많이 걸릴 수도 있다.

텍스트 데이터 같은 차원이 많은데 희소한 데이터에는 잘 작동하지 않습니다. ( 희소데이터가 많은 경우에는 잘 작동하지 못한다. )

그라디언트 부스팅 회귀 트리의 장단점

장점

연속적인 특성에서도 잘 작동한다. ( 연관된 특성이 많을 때 )

성능이 좋다.

단점

매개변수에 매우 민감하다.

n_estimators가 너무 큰 경우 과대적합의 위험성이 있다.

속도가 제일 느리다.

보통 설정하는 max_depth는 1~5이다. 5를 넘어가지 않도록 설정하는 것이 일반적

서포트 벡터 머신

초평면( Hyper Plain )에 대한 이해

라그랑주 승수

미분

벡터에 대한 이해

라그랑주 승수를 활용한 최적화 개념

SVM의 종류

선형 SVM(LinearSVC, LinearSVM)

데이터에 직선을 투영하는 방식

비선형 SVM(커널 SVM)

공통점 : 초평면을 활용하는 방식

SV (Support Vector)

훈련되어 있는 데이터 포인트에서 Support Vector를 선정하는 것이 SVM의 훈련과정

서포트 벡터의 개수와 범위를 지정하면서 복잡도를 조절

선형 SVM

직선을 이용해 분류 / 회귀를 하는 방식

다항식을 활용한 학습 방식

비선형 SVM ( 커널 SVM )

선형 SVM의 다차항 추가방식은 수학적인 기교를 활용하는 방식

커널 SVM은 수학적인 기교 보다는 커널 트릭(kernel trick)을 이용하는 방식

자주 사용되는 커널 - RBF(Radial Basis Function)을 활용 - 가우시안 커널

k(x1,x2)=exp(−γ||x1−x2||2)

SVM 모델이 학습하는 것 : 훈련 데이터 포인트가 두 클래스 사이의 결정 경계를 구분하는데 얼마나 중요한지를 배운다.

이 데이터 포인트를 서포트 벡터라고 한다.

가우시안 커널 폭의 거리는 최대 마진거리로 만들어 진다.

SVM의 하이퍼 파라미터

gamma

가우시안 커널폭의 역수 ( gamma가 커지면 커널폭이 작아지고, gamma가 작아지면 커널폭이 커진다.)

gamma 매개변수가 하나의 훈련 샘플에 미치는 영향의 범위를 설정

gamma가 커지면 복잡도가 올라간다.

gamma가 커지면 연관성 있는 데이터 포인트 끼리의 모임을 만든다.

C

서포트 벡터 선정에 영향을 미치는 규제 매개변수

각 데이터 포인트의 중요도 값을 제한합니다.

서포트 벡터는 == 포인트의 중요도

포인트 중요도 : 서포트 벡터로써, 결정 경계를 구성하는데 어떠한 역할을 하는지



​
