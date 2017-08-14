# New York Times 뉴스와 마켓 데이터를 사용하여 금융 시장의 예측 가능성 평가하기

이 개발자 과정에서는 Jupyter Notebook을 사용하여 IBM Power8 시스템에서 시계열을 활용한 머신러닝 예제를 보여줍니다. 이 노트북은 New York Times의 뉴스기사에 나타난 정서와 관련 마켓 데이터를 조사하여 재생 에너지 분야의 미래 금융 시장 가치에 대한 예측 가능성을 평가하는데 중점을 둘 것입니다.

이 과정을 마치면 다음을 이해할 수 있습니다:

* 다양한 외부 소스에서 구조화 된 데이터(Structured data) 추출 및 형식화
* 구조화되지 않은 데이터(Unstructured data)를 추출 및 형식화하고 IBM Watson Cognitive 서비스를 사용하여 데이터 감정을 분석
* Neutral network를 빌드하고 학습시킴
* Jupyter Notebooks의 결과 표시 및 공유

이 과정은 효과적으로 강력한 딥러닝 애플리케이션을 만들고자 하지만 시간이 부족하거나 데이터 사이언스 경험이 부족한 사람이 활용하기에 적합합니다.


![](doc/source/images/architecture.png)

## 사용된 컴포넌트

* [IBM Watson Natural Language Understanding](https://www.ibm.com/watson/developercloud/natural-language-understanding.html): 자연어 이해를 통해 컨텐츠에서 컨셉, 엔티티, 키워드, 카테고리, 정서, 감성, 관계, 의미적 역할과 같은 메타데이터를 추출하기 위한 블루믹스 서비스
* [IBM Power AI](https://www.ibm.com/ms-en/marketplace/deep-learning-platform): IBM Power System과 함께 가장 대중적인 머신 러닝 프레임워크들이 포함된 소프트웨어 플랫폼
* [IBM Power Systems](https://www-03.ibm.com/systems/power/): 오픈 테크놀로지 기술로 구축되고 업무용 응용 프로그램 용으로 설계된 IBM의 Power Architecture 기반 서버 라인
* [Nimbix Cloud Computing Platform](https://www.nimbix.net/): 엔지니어, 과학자 및 개발자가 클라우드에서 시뮬레이션을 작성, 계산, 분석 및 확장 할 수있는 HPC 및 클라우드 슈퍼 컴퓨팅 플랫폼

## 주요 기술

* [Data Science](https://medium.com/ibm-data-science-experience): 실시간 코드, 방정식, 시각화 및 설명 텍스트가 포함 된 문서를 만들고 공유 할 수있는 오픈 소스 웹 응용 프로그램
* [Tensorflow](https://www.tensorflow.org/): 데이터 플로우 그래프를 사용한 수치 계산을 위한 오픈 소스 소프트웨어 라이브러리

# 비디오 보기

[![](http://img.youtube.com/vi/1nnWj6W7QJI/0.jpg)](https://www.youtube.com/watch?v=1nnWj6W7QJI)

# 단계

이 개발자 과정을 설정하고 실행하려면 다음 단계를 따르십시오. 각 단계는 아래에서 자세하게 설명됩니다.

1. [평가판 Nimbix Cloud Platform 계정 등록](#1-register-for-a-trial-nimbix-cloud-platform-account)
2. [Nimbix UI 탐색](#2-navigating-the-nimbix-ui)
3. [TensorFlow 데모 배포 및 실행](#3-deploy-and-run-the-tensorflow-demo)
4. [Jupyter Notebook 접근 및 시작](#4-access-and-start-the-jupyter-notebook)
5. [Notebook 실행](#5-run-the-notebook)
6. [결과 분석](#6-analyze-the-results)
7. [저장 및 공유](#7-save-and-share)
8. [TensorFlow 데모 종료시키기](#8-shut-down-the-tensorflow-demo)

## 1. 평가판 Nimbix Cloud Platform 계정 등록

IBM과 Nimbux의 파트너쉽으로 PowerAI 플랫폼에서의 10시간 무료 컴퓨팅 시간을 제공하는 평가판 계정이 이 과정을 따라하는 개발자 들에게 제공됩니다.

등록 방법은 다음과 같습니다.:

* [IBM Cognitive 과정 데모 등록 페이지](https://www.nimbix.net/cognitive-journey)를 방문하여 등록 프로세스를 시작하십시오.

![](doc/source/images/nimbix-registration.png)

* 확인 이메일을 기다립니다. 이 프로세스는 자동하되어 있지 않아 검토하고 승인하는 데 최대 24 시간까지 소요될 수 있습니다.
* 확인 이메일을 받으면 24시간 이네에 제공된 링크를 클릭하여 등록 절차를 완료 하십시오.:

![](doc/source/images/nimbix-confirmation-1.png)

* 위의 링크를 클릭하면 계정 패스워드를 생성하는 페이지로 이동합니다.:

![](doc/source/images/nimbix-set-password.png)

> *참고:* "프로모션 코드"는 필요하지 않습니다.

* Nimbix에 로그인 하는 방법을 알려주는 확인 이메일을 기다립니다.:

![](doc/source/images/nimbix-registration-complete.png)

* [link](https://mc.jarvice.com?page=compute&team)를 클릭하면 Nimbix 로그인 페이지로 이동합니다.:

![](doc/source/images/nimbix-login.png)

## 2. Nimbix UI 탐색

Nimbix UI는 상단 패널에 두개의 주요 링크가 있습니다.

![](doc/source/images/nimbix-navigation.png)

* ``NIBMIX``를 클릭하면 사용 가능한 모드 목록이 드롭 다운으로 보여집니다. 한번 더 클릭하면 목록이 사라집니다. 위의 화면에서는 ``Dashboard`` 모드를 선택했습니다.

* 왼쪽에서 ``collapsible`` 아이콘을 클릭하면 선택된 모드와 관련된 뷰 목록이 드롭 다운으로 표시됩니다. 아이콘을 한번 더 클릭하면 목록이 사라집니다. 위의 화면에서는 ``Current Jobs`` 화면을 선택했습니다.

## 3. TensorFlow 데모 배포 및 실행

Nimbix에 로그인 했으면 IBM Power8 서버에 데모를 배포하십시오.

* ``Compute:All Applications`` 화면의 사용 가능한 앱 목록에서 ``TensorFlow Example Notebook``을 검색하여 선택하십시오.

![](doc/source/images/nimbix-search-page-demo.png)

* ``TensorFlow Example Notebook`` 애플리케이션 패널에서, ``TensorFlow`` 버튼을 클릭하십시오.:

![](doc/source/images/tensor-flow-demo-launch.png)

* ``TensorFlow`` 구성 패널에서 모든 기본 값을 적용하고 ``Submit`` 버튼을 누릅니다.:

![](doc/source/images/tensor-flow-demo-config.png)

> *참고:* "$3.80/hr" 요금은 무시하십시오. 평가판 계정을 사용하면 10시간의 무료 컴퓨팅 시간이 제공됩니다.

* 시작 되면, 다음과 같은 ``Dashboard`` 패널이 보여집니다. 서버의 ``Status``가 ``Processing``으로 바뀌면, 서버에 접근할 수 있습니다.

    ``Password`` 값을 메모해 두십시오.

* 노트북을 실행하려면 ``Click here to connect``를 클릭하십시오.

![](doc/source/images/tensor-flow-demo-click.png)

* 사용자 이름 ``nimbix`` 와 이 전에 제공된 패스워드를 사용하여 로그인 하십시오.

![](doc/source/images/tensor-flow-demo-login.png)

* 노트북 파일 목록에서 ``MLDL-demo``를 클릭하십시오.

![](doc/source/images/tensor-flow-files-1.png)

## 4. Jupyter Notebook 접근 및 시작

주피터 노트북을 시작하려면 ``Clean_Energy_Watson_V1.0.ipynb`` 링크를 클릭하십시오.

![](doc/source/images/tensor-flow-files-2.png)

![](doc/source/images/nb-start-page.png)

## 5. Notebook 실행

노트북을 실행시키면 노트북의 각 코드 셀이 위에서 아래로 순서대로 실행됩니다.

각 코드 셀은 선택 가능하며 왼쪽 여백에 태그가 붙습니다. 태그 형식은 `In [x]:` 입니다. 노트북의 상태에 따라 `x` 는 다음과 같이 표시됩니다.:

* 공백은 한번도 실행된 적이 없는 셀을 나타냅니다.
* 숫자는 이 코드 단계가 실행된 상대적 순서를 나타냅니다.
* `*` 은 그 셀이 현재 실행중임을 나타냅니다.

노트북에서 코드 셀을 실행시키는 방법은 여러가지가 있습니다.:

* 한번에 하나의 셀을 실행
  * 셀을 선택하고 툴바에 있는 `Play` 버튼을 클릭합니다.
* 순서대로 배치 모드로 실행
  * `Cell` 메뉴바에 몇가지 옵션이 있습니다. 예를들어, `Run All` 옵션으로 노트북에 있는 모든 셀을 실행시킬 수 있습니다. `Run All Below` 옵션으로 현재 선택된 첫번째 셀부터 실행하고 다음 계속되는 모든 셀을 계속 실행할 수 있습니다. 

참조:

- 셀 `[4]` 부연 설명: 이 개발자 과정에서는 이미 수집된 주식 시장 데이터를 가져옵니다. 이는 노트북에서 수행할 수 있지만 유료 금융 웹 사이트(예: Bloomberg)의 권한을 필요로 합니다.

- 셀 `[5]` 부연 설명: 노트북 처리 시간을 빠르게 하기 위해, New York Times 데이터는 이미 JSON 파일로 수집되어 저장돼 있는 것을 노트북에서 가져와서 사용합니다.

- 이 개발자 과정은 Google Cloud Platform 예제를 바탕으로 만들어 졌습니다. 구글 예제에 대한 문서는 https://cloud.google.com/solutions/machine-learning-with-financial-time-series-data 에서 확인할 수 있습니다. "IBM 데모"와 기존 "Google 데모"의 차이점은 다음 테이블에서 확인하십시오.:

![](doc/source/images/demo-diffs.png)

## 6. 결과 분석

노트북을 실행한 결과는 코드와 함께 또는 코드 없이 공유할 수 있는 레포트 입니다. 코드는 어떻게 결론에 이르렀는지를 보고 싶어 하는 사람에게 공유하면 좋습니다. 텍스트, 코드 그리고 결과/차트는 단일 웹 페이지로 결합됩니다. 코드를 보고 싶어하지 않는 사람에게는 텍스트와 결과/차트만 보여주는 웹 페이지로 공유할 수 있습니다.

이 개발자 과정에서 그래프와 차트는 나스닥 청정 에너지 지수의 종가가 New York Times나 국내외의 기타 금융 시장과 같은 다양한 데이터 소스를 조사하여 예측될 수 있다는 것을 증명하려고 시도합니다. 이러한 시장에는 다음을 포함합니다.:

- Australian Clean Tech Index (asx_cti)
- Germany DAX (dax_eusdn)
- UK FTSE100 (ftse-eo100)
- UK Credit Suisse (n8wh)
- US First Trust Nasdaq Clean Edge ETF (qcln and cels)
- US S&P Global Clean Energy Index (icln and sp_gtced)
- US Equity Uncertainty Index (dei)

#### 데이터 수집

이 노트북은 데이터 수집 및 구조화로 시작합니다.:

* 3년간의 시장 재무 데이터를 수집하고 병합합니다.

* New York Times로부터 3년간의 "green energy"에 대한 기사를 수집합니다. 이 데이터를 Watson Natural Language Understanding 서비스로 분석하여 정서 데이터를 수집합니다. - 구체적으로, 상대적으로 긍정적인지 부정적인지에 대한 점수를 각 기사에 매깁니다.

![](doc/source/images/sentiment-values.png)

#### 데이터 분석

그런 다음 노트북은 EDA (탐색 데이터 분석, exploratory data analysis) 방법을 활용하여 데이터에서 상관 관계를 찾습니다. 이 결과는 다음과 같습니다:

* 3 년 동안 모든 지수 사이에 상관 관계가 있었습니다.

![](doc/source/images/3-year-span.png)

* 어떠한 인덱스의 현재 값과 지연 값 사이에는 상관 관계가 있습니다.

![](doc/source/images/correlation-data.png)

* 같은 날에 사용 가능한 다른 인덱스(즉, 미국 이외의 인덱스)의 종가와 상관 관계가 있는 2개의 미국 인덱스(qcln 과 icln)가 있습니다.

![](doc/source/images/scatter-graph.png)

EDA의 최종 분석은 다음과 같습니다.:
- 같은 날 호주 지수의 종가는 나스닥 에너지 지수 종가에 대한 강력한 예측 지표이다.
- 유럽 지수들은 나스닥 에너지 지수 종가의 주요한 예측 지표이다.
- 전날의 지수들은 나스닥 에너지 지수에 대해 좋은 예측 지표가 아니었다.

#### 데이터 학습 및 테스트

데이터에서 이 상관관계를 확인한 후, 이 노트북은 TensorFlow와 IBM PowerAI 머신 러닝 프레임워크를 사용하여 데이터를 학습 및 테스트 합니다.

여러 모델을 사용하여 데이터에 대해 수십만 번의 반복 작업을 수행한 후, 이 노트북은 나스닥 지수가 특정 날짜에 올라가거나 내려가는 것을 예측하는 데에 70%의 성공률을 달성할 수 있습니다.

## 7. 저장 및 공유

### 작업 저장 방법:

이 노트북은 Nimbix Cloud 서버에서 일시적으로 실행되므로 노트북을 저장하고 공유하는 옵션이 제한됩니다.

`File` 메뉴에 다음과 같은 옵션이 있습니다.:

* `Download as...` 로컬 시스템에 노트북을 다운로드합니다.
* `Print Preview` 노트북의 현재 상태를 인쇄합니다.

## 8. TensorFlow 데모 종료시키기

TensorFlow 데모가 완료 되었으면 Nimbix Cloud Platform의 리소스를 확보하기 위해 서버를 종료시켜야 합니다. 무료 평가판 등록은 10시간의 컴퓨팅 시간만을 제공합니다.

* Nimbix의 ``Dashboard:Current Jobs`` 화면에서, ``Shutdown``버튼을 클릭하십시오.

![](doc/source/images/tensor-flow-demo-kill.png)

<!--
# Sample output

The following is a sample data visualization with code
 ![](doc/source/images/output.png)
 For a full example without code see [`data/examples/sample_output.pdf`](data/examples/sample_output.pdf).
-->

# 문제 해결(Troubleshooting)

[DEBUGGING.md를 참조하십시오.](DEBUGGING.md)

# 라이센스(License)

[Apache 2.0](LICENSE)
