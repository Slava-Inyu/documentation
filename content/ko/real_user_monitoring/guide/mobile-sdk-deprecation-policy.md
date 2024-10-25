---
further_reading:
- link: /real_user_monitoring/explorer
  tag: 설명서
  text: 탐색기에서 RUM 데이터 시각화
- link: /real_user_monitoring/guide/mobile-sdk-upgrade
  tag: 설명서
  text: Datadog 모바일 SDK 업그레이드
title: RUM 모바일 SDK 지원 중단 정책
---

## 개요

Datadog은 강력한 최신 모바일 개발 생태계를 유지하는 것이 중요하다는 점을 잘 알고 있습니다. 다음 모바일 지원 중단 정책으로 Datadog 모바일 SDK의 지속적인 개선 및 안정성을 보장합니다. 이러한 지원 중단 정책은 업계 모범 사례에 부합하는 동시에 고객님께 합리적 전환 기간을 보장해 드립니다.

## 버전 관리
Datadog 모바일 SDK는 [시맨틱 버전 관리][1]를 따릅니다. 주요버전의 변경은 공개 API 또는 동작에 대한 하위 호환 변경이 아님을 뜻합니다.

주요 버전에서 다음 버전으로 업데이트할 때는 [SDK 업그레이드 지침][2]을 면밀히 준수하는 것이 중요합니다.

## 주요 SDK 버전 수명 주기

### 일반 공개(GA) 릴리스

* **시작일**: GA 릴리스는 SDK의 주요 버전이 공식적으로 출시되어 제공되는 시점을 의미합니다.
* **지원 수준**: GA 단계에서는 새로운 기능 추가 및 버그 수정을 포함하여 주요 버전이 완벽하게 지원됩니다.

### 지원 중단 단계

* **시작일**: 지원 중단 단계는 후속 주요 GA 버전이 출시된 직후부터 시작됩니다.
* **지원 수준**: 이 단계에서는 심각한 버그 수정과 지원 중단된 주요 버전의 안정성을 보장하는 데 중점을 둡니다. 새로운 기능 추가 계획은 없으나 심각한 문제 해결 지원은 계속 제공합니다.

### 지원 종료 (EOS)

* **시작일**: 후속 주요 GA 버전이 출시된 후 6개월이 지나면 지원 종료(EOS) 단계가 시작됩니다.
* **지원 수준**: 이 단계에서는 EOS 주요 버전에 대한 지원을 중단합니다. 해당 버전에 대한 버그 수정이나 업데이트는 제공되지 않습니다.

## 최소 지원 기간
마이그레이션에 필요한 합리적 소요 기간을 보장하고 계획을 세울 수 있도록 각 주요 버전에 최소 지원 기간을 보장해 드립니다. 모든 주요 버전은 GA 출시 후 최소 6개월 동안 완벽 지원됩니다.

해당 지원 기간 동안에는 심각한 문제를 해결하는 것 외에도 새로운 기능 추가 및 버그 수정이 제공됩니다.

## 참고 자료

{{< partial name="whats-next/whats-next.html" >}}

[1]: https://semver.org/
[2]: /ko/real_user_monitoring/guide/mobile-sdk-upgrade