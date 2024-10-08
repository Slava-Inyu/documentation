---
algolia:
  tags:
  - 제한없는 메트릭
aliases:
- /ko/metrics/faq/metrics-without-limits/
- /ko/metrics/guide/metrics-without-limits-getting-started/
further_reading:
- link: https://www.datadoghq.com/blog/metrics-without-limits
  tag: 블로그
  text: 제한없는 메트릭 수집TM을 통한 동적 커스텀 메트릭 볼륨 조절
- link: /observability_pipelines/guide/custom-metrics-governance
  tag: 설명서
  text: 커스텀 메트릭 관리를 위해 Observability Pipelines 사용
title: 제한없는 메트릭 수집TM
---

## 개요

제한없는 메트릭 수집TM은 커스텀 메트릭 수집 및 인덱싱을 분리하여 유연성을 제공하는 한편 커스텀 메트릭 볼륨을 관리할 수 있도록 해줍니다. 조직에 가치 있는 커스텀 메트릭 태그에만 지불하면 됩니다.

제한없는 메트릭 수집TM은 인앱에서 모든 메트릭 유형에서 태그를 설정할 수 있도록 해줍니다. 또한 코드를 변경하거나 다시 배포할 필요 없이 개수, 속도 및 게이지 총계를 커스터마이즈할 수 있습니다. 제한없는 메트릭 수집TM을 사용해 인앱 태그 허용 목록을 설정하고 Datadog 플랫폼 전반에서 쿼리 가능하도록 할 수 있습니다. 이는 자동으로 애플리케이션 수준 또는 비즈니스 메트릭(예: `host`)에 연결된 불필요한 태그를 제외합니다. 이 기능은 [메트릭 요약][1] 페이지에 나와 있습니다.

이 페이지는 관측 가능성(observability) 예산 내에서 커스텀 메트릭 볼륨을 관리할 수 있도록 제한없는 메트릭 수집TM의 핵심 구성 요소를 알려줍니다. 

### 태그 설정

아무 메트릭 이름을 클릭하면 관련 상세 정보 사이드 패널이 열립니다. 그러면 **태그 관리** -> **"태그 포함..."**을 클릭하여 대시보드와 모니터에서 쿼리 가능하도록 하려는 태그를 설정합니다. 태그 설정 모달에는 기본적으로 대시보드, 노트북과 모니터와 API를 통해 지난 30일간 활성 쿼리된 태그 허용 목록(이 표시되어 있습니다(아이콘과 함께 파란색으로 표시). 또한 자체적인 추가 태그를 포함할 수도 있습니다. 이 잠재적 태그 설정에 따라 인덱스된 커스텀 메트릭의 새로운 추정 볼륨이 표시되면 **저장**을 선택합니다.

{{< img src="metrics/mwl_tag_config.mp4" alt="태그 설정" video=true >}}


태그 설정을 [생성][2], [편집][3] 및 [삭제][4]할 수 있는 API도 존재합니다. 잠재적 설정 영향을 추정하는 [API][5]도 있습니다.

개수, 속도 및 게이지에 대한 태그를 설정할 때 가장 자주 쿼리된 시간/공간 집계 조합을 기본적으로 쿼리에 사용할 수 있습니다.

### 집계 상세 검색 및 최적화

개수, 게이지 및 속도 메트릭에서 더 많은 [메트릭 총계][6]를 사용하도록 설정하여 커스텀 메트릭을 상세하게 조정할 수 있습니다. 쿼리의 수학적 정확도를 유지하기 위해 Datadog는 제공된 메트릭 유형에 대해 가장 자주 쿼리된 시간/공간 집계 조합만을 저장합니다.

- 설정된 개수와 속도는 SUM을 사용해 시간/공간에서 쿼리 가능합니다.
- 설정된 게이지는 AVG를 사용해 시간/공간에서 쿼리 가능합니다.

에이전트 또는 코드 수준 변경 없이 언제든지 집계를 추가하거나 제거할 수 있습니다.

태그 설정 모달에는 기본적으로 대시보드, 노트북과 모니터와 API를 통해 지난 30일간 활성 쿼리된 태그 허용 목록(이 표시되어 있습니다(아이콘과 함께 파란색으로 표시). 또한 자체적인 추가 태그를 포함할 수도 있습니다. 


### 한 번에 여러 메트릭 설정

[대량 메트릭 태그 설정 기능][7]을 사용해 커스텀 메트릭 볼륨을 최적화합니다. 메트릭 요약에서 **태그 포함...**을 클릭하여 메트릭에 대한 네임스페이스를 지정할 수 있습니다. 그런 다음 동일한 태그 허용 목록에서 네임스페이스 접두사와 일치하는 모든 메트릭을 설정할 수 있습니다.

## 제한없는 메트릭 수집TM 빌링

태그와 집계를 설정하면 쿼리할 수 있는 커스텀 메트릭을 통제할 수 있습니다. 궁극적으로 커스텀 메트릭의 빌링 가능한 개수가 줄어듭니다. 제한없는 메트릭 수집TM은 인덱스 비용과 수집 비용을 분리합니다. Datadog에 모든 데이터를 계속 전송(모든 수집 대상)하고 Datadog 플랫폼에서 쿼리 가능하도록 하려는 태그 허용 목록을 지정할 수 있습니다. Datadog가 설정한 메트릭에 대해 수집하는 데이터 볼륨이 사용자가 인덱스하는 더 작은 볼륨과 다른 경우, 메트릭 요약 페이지와 사용량 페이지에서 두 개의 별도 볼륨을 확인할 수 있습니다.

- **수집된 커스텀 메트릭**: 모든 수집 태그(코드를 사용해 전송됨)를 기준으로 한 커스텀 메트릭 원래 볼륨입니다.
- **인덱스된 커스텀 메트릭**: Datadog 플랫폼에서 쿼리 가능한 커스텀 메트릭 볼륨(모든 제한없는 메트릭 수집TM 설정 기준)입니다.

**참고: 설정된 메트릭만 수집된 커스텀 메트릭 볼륨에 기여하게 됩니다.** 제한없는 메트릭 수집TM으로 메트릭이 설정되지 않은 경우, 인덱스된 커스텀 메트릭 볼륨에 대해서만 요금이 부과됩니다.

[커스텀 메트릭 빌링][8]에 대해 자세히 알아보세요.

## 제한없는 메트릭 수집TM 시작하기

1. 메트릭 요약 페이지나 [API]를 사용하여 [계획 및 사용량 페이지][9]에서 상위 20개 메트릭을 설장하세요[2].
   대량 메트릭 구성(`*` 구문)을 사용하여 여러 메트릭에서 빠르게 태그를 설정할 수 있습니다. Datadog에서 대량 설정 작업이 완료되면 알림을 전송합니다.

**참고:** [태그 설정 생성 API][2] 를 사용하는 경우 먼저 [태그 설정 카디널리티 예측 도구 API][5]를 사용해 태그 설정 생성 전 태그 설정의 잠재적 영향을 검증합니다. UI 또는 예측 도구 API가 수집된 것보다 더 큰 수의 인덱스 숫자를 반환하면 태그 설정을 저장하지 마세요.

2. 빈 태그 설정을 통해 쿼리되지 않은 메트릭을 설정하세요.

   팀이 Datadog 플랫폼에서 절대 쿼리되지 않는 메트릭을 계속 정리해 감에 따라 빈 태그 허용 목록으로 태그를 설정하여 이러한 쿼리되지 않는 메트릭의 비용을 즉시 최소화할 수 있습니다.

   조회되지 않는 메트릭 보고서는 고객 성공 관리자에게 물어보세요.

3. 사용량과 빌링을 검토하세요. 메트릭을 설정한 후 변경에 대한 영향을 세 가지 방법으로 측정할 수 있습니다.

   - 설정을 저장하기 전 태그 설정 카디날리티 측정 도구는 인덱스된 커스텀 메트릭의 예측 수를 반환합니다. 이 수는 수집된 커스텀 메트릭 볼륨보다 작아야 합니다.
   - 설정 저장 후 메트릭 요약 상세 정보 사이드 패널에 수집된 커스텀 메트릭 볼륨보다 작은 인덱스된 커스텀 메트릭이 표시됩니다.
   - 설정을 저장한 후 24시간이 지나면 또한 계획 및 사용량 페이지의 **상위 커스텀 메트릭** 표에서 영향을 확인할 수 있습니다. 표의 **월간 누계** 탭과 **가장 최근 날짜** 사이에서 커스텀 메트릭 볼륨 감소를 확인할 수 있습니다.

## 모범 사례

- 실시간 [추정 커스텀 메트릭 사용량][10] 메트릭에서 알림을 설정할 수 있습니다. 그러면 커스텀 메트릭 급증과 설정을 연계할 수 있습니다.

- 제한없는 메트릭 수집TM의 [역할 기반 액세스 제어][11]를 통해 빌링에 영향을 줄 수 있는 이 기능에 대한 사용자 권한을 제어할 수 있습니다.

- 감사 이벤트를 통해 커스텀 메트릭 급증과 연계할 수 있는 태그 설정 또는 백분위수 집계를 추정할 수 있습니다. [이벤트 스트림][12]에서 "태그:감사" 및 "쿼리 가능한 태그 설정" 또는 "백분위수 집계"를 검색합니다.

\*제한없는 메트릭 수집은 Datadog, Inc의 등록 상표입니다.

## 참고 자료

{{< partial name="whats-next/whats-next.html" >}}

[1]: https://app.datadoghq.com/metric/summary
[2]: /ko/api/latest/metrics/#create-a-tag-configuration
[3]: /ko/api/latest/metrics/#update-a-tag-configuration
[4]: /ko/api/latest/metrics/#delete-a-tag-configuration
[5]: /ko/api/latest/metrics/#tag-configuration-cardinality-estimator
[6]: /ko/metrics/#time-and-space-aggregation
[7]: /ko/metrics/summary/#configuration-of-multiple-metrics
[8]: /ko/account_management/billing/custom_metrics/
[9]: https://app.datadoghq.com/billing/usage
[10]: /ko/account_management/billing/usage_metrics/
[11]: /ko/account_management/rbac/permissions/?tab=ui#metrics
[12]: https://app.datadoghq.com/event/stream