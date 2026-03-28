# Hysteria

::: tip
При использовании `hysteria protocol` по умолчанию включен `quic native udp`.

При использовании `hysteria inbound` параметр `auth` будет переопределен параметром `clients` (если он существует).

Возможность проксирования `udp` при использовании других `protocol` зависит от того, поддерживает ли данный `protocol` `uot`.

Включение `finalmask.udp` нарушит работу маскировки страницы `masquerade`.
:::

## HysteriaObject

`HysteriaObject` соответствует параметру `hysteriaSettings` в конфигурации транспортного уровня.

```json
{
  "version": 2,
  "auth": "password",
  "udpIdleTimeout": 60,
  "masquerade": {
    "type": "",

    "dir": "",

    "url": "",
    "rewriteHost": false,
    "insecure": false,

    "content": "",
    "headers": {
      "key": "value"
    },
    "statusCode": 0
  }
}
```

> `version`: number

Версия Hysteria, должна быть 2.

> `auth`: string

Пароль аутентификации Hysteria, должен совпадать на сервере и клиенте.

> `udpIdleTimeout`: number

Время ожидания простоя для отдельного соединения `udp`. Если значение слишком велико, оно может не соблюдаться строго, и соединение может быть прервано `policy` раньше этого времени.

> `masquerade`: [MasqObject](#MasqObject)

Маскировка страницы `http3`.

### MasqObject

```json
{
  "type": "",

  "dir": "",

  "url": "",
  "rewriteHost": false,
  "insecure": false,

  "content": "",
  "headers": {
    "key": "value"
  },
  "statusCode": 0
}
```

> `type`: "file" | "proxy" | "string"

Если не заполнено, по умолчанию используется страница 404.

> `dir`: string

Параметр конфигурации при `type` равном `file`.

> `url`: string

Параметр конфигурации при `type` равном `proxy`.

> `rewriteHost`: false |  true

Параметр конфигурации при `type` равном `proxy`.

> `insecure`: false |  true

Параметр конфигурации при `type` равном `proxy`.

> `content`: string

Параметр конфигурации при `type` равном `string`.

> `headers`: map{ string, string }

Параметр конфигурации при `type` равном `string`.

> `statusCode`: int

Параметр конфигурации при `type` равном `string`.
