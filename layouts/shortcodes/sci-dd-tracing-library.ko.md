Go의 경우 [버전 1.18](https://tip.golang.org/doc/go1.18)부터 이진으로 버전 관리 정보를 포함합니다. Datadog 추적 라이브러리에서 이 정보를 사용해 텔레메트리를 최신 커밋 SHA와 리포지토리 URL로 태그합니다.

이 방법을 사용하려면 서비스가 다음 요구 사항을 충족해야 합니다.

* Go 버전 1.18 이상
* 서비스가 go 모듈로 구축되고 모듈 경로가 코드의 리포지토리 URL이어야 함
