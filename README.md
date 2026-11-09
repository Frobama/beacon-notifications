# beacon-notifications

Servicio de **notificaciones y escalamiento** de Beacon: turnos on-call, políticas de escalamiento y envío de avisos.

| | |
|---|---|
| Lenguaje | C# (.NET 8) |
| Base de datos | MongoDB |
| Comunicación | NATS (no usa gRPC) |
| Escucha | `incident.opened`, `incident.acknowledged`, `incident.resolved` |
| Publica | `escalation.triggered`, `notification.sent` |
| Responde (request/reply) | `notifications.oncall.get`, `notifications.policies.list`, `notifications.schedule.create` |

## Contratos

```bash
make proto
```

Genera en `gen/csharp` (no versionado). Detalle de subjects en [`beacon-contracts/docs/nats-subjects.md`](https://github.com/Frobama/beacon-contracts/blob/main/docs/nats-subjects.md).

## Entorno local

MongoDB y NATS corren desde [`beacon-infra`](https://github.com/Frobama/beacon-infra) (`make up`):

```text
mongodb://beacon:beacon@localhost:27017/notifications?authSource=admin
nats://localhost:4222
```

## Estado

Fase 0: solo generación de contratos. El servicio se implementa en la Fase 2.
