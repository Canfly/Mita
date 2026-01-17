Status: Draft
Invariants:
- Ledger хранит только метаданные - без тел артефактов.
- События неизменяемы - только добавление.

# Interaction Ledger Spec

Version: 0.1.0

Interaction Ledger - это Event Registry. Он хранит метаданные взаимодействий и ссылки на оффчейн артефакты.

## Event Envelope

| Поле | Тип | Описание |
| --- | --- | --- |
| event_id | CID | Уникальный идентификатор события. |
| event_type | string | Тип события - Lumen, Pact, Aegis и т.д. |
| actor_id | string | Идентификатор участника. |
| timestamp | int64 | Время события - Unix epoch. |
| domain_id | string | Guardian домен политики. |
| refs | list<CID> | Ссылки на связанные события. |
| payload_cid | CID | Ссылка на оффчейн данные - опционально. |
| signatures | list | Подписи участников и узлов. |

## Правила
- Все события подписываются участниками.
- Ledger не хранит файлы - только ссылки и метаданные.
- Публичность ограничена - по правилам домена.
