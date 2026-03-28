# Hysteria

::: tip
Протокол `hysteria` сам по себе не имеет аутентификации, `clients` работают только при использовании транспора `hysteria`.
:::

## InboundConfigurationObject

```json
{
  "version": 2,
  "clients": [
    {
      "auth": "5783a3e7-e373-51cd-8642-c83782b807c5",
      "level": 0,
      "email": "love@xray.com"
    }
  ]
}
```

> `version`: number

Версия Hysteria, должна быть 2.

> `clients`: \[ [ClientObject](#clientobject) \]

Массив, представляющий группу пользователей, авторизованных на сервере.

### ClientObject

```json
{
  "auth": "5783a3e7-e373-51cd-8642-c83782b807c5",
  "level": 0,
  "email": "love@xray.com"
}
```

> `auth`: string

Строка произвольной длины.

> `level`: number

Уровень пользователя. Соединение будет использовать [локальную политику](../policy.md#levelpolicyobject), соответствующую этому уровню пользователя.

Значение level соответствует значению `level` в [policy](../policy.md#policyobject). Если не указано, по умолчанию равно 0.

> `email`: string

Email пользователя, используется для разделения трафика различных пользователей (будет отображаться в логах и статистике).
