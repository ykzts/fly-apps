# fly-apps

Fly.ioで動かすアプリケーションの設定を管理するリポジトリです。

## Apps

| App | Fly.io app | Description |
| --- | --- | --- |
| Uptime Kuma | `ykzts-uptime` | 外形監視 |
| Uptime Kuma DB | `ykzts-uptime-db` | Uptime Kuma 用 MariaDB |

## Deploy

```console
fly deploy --config apps/uptime-kuma/fly.toml --app ykzts-uptime ./apps/uptime-kuma
```

```console
fly deploy --config apps/uptime-kuma-db/fly.toml --app ykzts-uptime-db ./apps/uptime-kuma-db
```

## Secrets

パスワードなどは`fly.toml`に含めず、Fly.ioのsecretsで管理します。

```console
fly secrets set KEY=value --app <app>
```

## Notes

- Uptime Kumaは`ykzts-uptime-db`のMariaDBを利用します。
- DB はFly.io private network経由で接続します。
