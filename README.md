# 미리수(水)

## Abstract

Recently, due to abnormal climate conditions, South Korea has experienced an increase in the frequency of heavy rainfall, leading to an increase in instances of river overflow and low-lying area inundation. However, predicting the locations and timing of floods due to the variability of climate conditions is a challenging task that requires a substantial amount of data and complex calculations. Thus, in this study, we utilized data from the Geumgang Flood Control Office spanning from 2017 to 2021 to predict the water levels at the Gapcheon Mannyeon Bridge in 2022. Furthermore, in this study, we investigated the interrelationship among precipitation, volume flow rate, and water levels in order to achieve low error rates with a limited amount of data. Both the Prophet and LightGBM models were employed in machine learning, and the accuracy of predicted river water levels was evaluated using metrics such as Mean Absolute Percentage Error(MAPE) and Root Mean Square Error (RMSE). The evaluation of the trained models revealed that both the Prophet and LightGBM models demonstrated a low level of error in predicting river water levels. On average, the MAPE value was 3.02%, the MSE value was 0.43%, and the RMSE value was 6.49%. These results suggest that the developed models can be effectively used to predict river water levels, and this study highlights an intuitive and simple approach to predicting water levels in the Gapcheon area.Also, it provides guidelines for creating a water level prediction model with a low error rate, including when the amount of data to be learned is small.

> Key Words: Machine Learning, Water Level, Precipitation, Volume Flow Rate, Correlation


## Introduction

최근 이상기후로 인해 전 세계에서 다양한 형태의 자연재해로 인한 심각한 피해가 보고되고 있다. 특히, 이러한 자연재해 중 호우로 인한 저지대 침수 현상은 인명, 재산 및 사회 경제 시스템에 대규모로 피해를 야기하며 가장 파괴적인 영향을 미친다. 또한, 그 영향은 더 이상 지역적이거나 시간적으로 제한되지 않고 전 세계적인 문제로 진화하고 있다.

&nbsp;특히, 한국처럼 인구 밀도가 높은 지역에서는 호우로 인한 침수가 더욱 심각한 문제로 부상하고 있다. 국가적 차원에서도 이러한 문제에 직면하고 있음에도 불구하고 도시 하천과 같은 인구 밀집지역에서의 범람은 대규모 홍수 피해로 이어지고 있다. 최근의 사례로는 2020년 한반도 폭우 사태와 2022년 중부권 폭우 사태가 있다. 이러한 사례들은 홍수로 인한 하천의 범람을 시작으로 산사태, 저지대 침수 등 다양한 형태의 피해가 연쇄적으로 발생했다.

&nbsp;기후 변화(Climate Change)로 인한 홍수의 피해를 예방하고 최소화하기 위해서는 수문학적 관점(Hydrological Perspective)에서의 단기 및 장기적인 예측이 매우 중요하기 때문에 다양한 예측 모델에 대한 연구가 활발히 진행되고 있다(Kim et al., 2022; Kim et al., 2022; Jung et al., 2017; Osman et al., 2018; Taylor and Letham., 2017). 그러나 홍수 발생 위치와 시기에 대한 예측은 기후 조건의 동 적 성질 때문에 근본적으로 복잡하다. 따라서 오늘 날 주요한 홍수 예측 모델은 데이터에 특화되어 단순화된 가정들이 포함되며, 물리적 과정과 복잡 한 수학적 식을 모방하기 위해 결정론적, 경험적, 확률적 기법들을 활용하여 이루어진다. 물리 기반 모델은 폭풍(Costabile and Macchione., 2012; Costabile and Macchione., 2013), 하천 및 해양(Le et al., 2019; Borah., 2011)과 같은 수문학적 관점에 서 예측하는데 사용되었다. 그러나 물리 모델은 다 양한 수문 시스템을 예측하기 위해서 많은 데이터 를 확보하는데 한계가 있으며, 계산의 복잡성 때문 에 예측에 필요한 수문학적 매개 변수들을 고려하 기에 어려웠다.

&nbsp;홍수 예측 모델 개발을 위한 데이터 확보와 계 산의 복잡성과 같은 한계를 극복하기 위해, 우리는 제한된 시계열 데이터를 활용하여 Prophet 모델과 LightGBM과 같은 기계학습(Machine Learning) 알고 리즘을 구축했다. 우리가 직면한 주요 과제는 제한 된 시계열 데이터를 활용해 기계학습(Machine Learning)모델을 학습시키고 갑천의 수위를 예측하 기 위한 단순법(Simple Method)을 찾는 것이다. 특 히 우리는 데이터의 부족함을 극복하고 모델의 정 확도를 향상시키는데 초점을 맞추고 있다. 이를 위 해 2017년부터 2021년까지의 강수량(Precipitation), 수위(Water Level), 체적유량(Volume Flow Rate)의 상호 연관성을 파악하여 최종적으로 미래의 특정 시점의 수위를 예측했다. 예측한 수위의 성능 평가 를 위해서 우리는 평균 절대 백분율 오차(Mean Absolute Percentage Error, MAPE), 평균 제곱 오차 (Mean Sqaure Error, MSE), 평균 제곱근 오차(Root Mean Square Error, RMSE) 세 가지를 평가 지표로 선정하였다. 이 지표들을 통해 실제 수위와 예측된 수위 간의 오차를 정량화하고, 모델의 예측 성능을 평가했다.

## Overview

본 연구의 구성요소 및 그 순서도(Flow Chart)는 다음 Fig. 1과 같다.

![Figure 1](./assets/Figure-1.png)

<p align="center">
Fig. 1. Flow Chart for Building Flood Prediction Method
</p>



## References





> 본 글과 저장소(Repository)의 저작권은 김종혁, 이성지, 김민중, 나종열에게 있습니다. 무단 도용, 배포, 복제를 금합니다.

> 필요하신 자료나 정보가 있으신 경우, 본 논문의 교신저자(Corresponding Author)인 나종열의 [이메일](najyeol99@gmail.com)로 연락주시기 바랍니다.