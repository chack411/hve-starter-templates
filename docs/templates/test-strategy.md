# テスト方針

## 確認したい品質

| Goal | Related requirement or risk | Evidence required |
| --- | --- | --- |
| | `REQ-NNN` or `RISK-NNN` | |

## テストの種類

| Level | Scope | Owner | Environment | Trigger | Exit criterion |
| --- | --- | --- | --- | --- | --- |
| Unit | | | | | |
| Component or integration | | | | | |
| Contract | | | | | |
| End-to-end | | | | | |
| Non-functional | | | | | |

## 要件ごとのテスト

| Requirement | Scenarios | Test level | Test ID | Automation status |
| --- | --- | --- | --- | --- |
| REQ-001 | Normal, error, boundary, authorization | | `TEST-NNN` | Planned |

## テストデータと実行環境

- Data generation and isolation:
- Sensitive data policy:
- External dependency strategy:
- Environment parity and reset:
- Time, locale, and concurrency handling:

## 速さ、安全性、使いやすさなどの確認

| Attribute | Target | Method | Environment | Owner |
| --- | --- | --- | --- | --- |
| Performance | | | | |
| Accessibility | | | | |
| Security | | | | |
| Reliability and recovery | | | | |

## 作業を止める条件

| Gate | Required checks | Blocking threshold | Evidence location |
| --- | --- | --- | --- |
| Pull request | | | |
| Release candidate | | | |

## 完了チェック

- [ ] すべての確認済み要件と重大なリスクに、確認方法が決まっている。
- [ ] Normal, error, boundary, authorization, and recovery scenarios are considered.
- [ ] Test data is reproducible and contains no production secrets or personal data.
- [ ] Blocking thresholds and owners are explicit.

## 次にすること

| おすすめ | 入力する内容 | 回答後に始まる作業 | プロンプト候補 |
| --- | --- | --- | --- |
| テスト方針を確認する | `[必須テスト、利用できる環境、止める条件]` | 実装タスクへテストを割り当てる | `/12-break-down-implementation` |

## 人による確認

| 確認する人 | 結果 | 日付 | メモ |
| --- | --- | --- | --- |
| | 確認待ち | | |
