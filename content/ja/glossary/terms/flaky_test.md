---
core_product:
- ci-cd
title: 不安定なテスト
---
不安定なテストとは、同じコミットに対して複数回テストを実行したときに、成功と失敗の両方のステータスを示すテストのことです。あるコードをコミットして CI を通して実行するとテストが失敗し、再度 CI を通して実行するとテストが成功した場合、そのテストはコードの品質を証明するものとしては信頼できません。詳しくは<a href="/tests/search/#test-results">ドキュメントを参照してください</a>。