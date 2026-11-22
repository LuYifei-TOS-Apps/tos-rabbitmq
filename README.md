# RabbitMQ for TOS 7

此应用使用 RabbitMQ 4.4.1 的官方镜像，在 x86_64 和 aarch64 TNAS 上提供单节点消息代理与管理控制台。[镜像说明](https://hub.docker.com/_/rabbitmq)

## 连接

1. 启动 TOS 的 Docker Engine 和 RabbitMQ，等容器状态健康。
2. 在 TOS Docker 管理器打开 RabbitMQ 容器的 root 终端，执行 `cat /var/lib/rabbitmq/.tos-admin-password`，取得首次启动生成的口令。
3. 打开 TOS 桌面入口，或在可信网络访问 `http://<NAS-IP>:15672/`。管理用户名为 `tosadmin`。为业务应用分别创建 RabbitMQ 用户并按需要授权虚拟主机。
4. AMQP 客户端连接 `<NAS-IP>:15673`。网络端口默认使用明文协议，请限制访问范围。若已在管理控制台更改账号口令，后续使用新的口令。

## 数据与备份

`/var/lib/rabbitmq` 的应用数据目录保存节点状态、持久化消息和初始密码文件。采用固定节点名 `rabbit@rabbitmq`。要在重启后保留消息，请使用持久队列、持久消息和发布确认。备份前可导出拓扑定义，或停止应用后复制应用数据目录并限制副本的访问权限。[RabbitMQ 备份与恢复](https://www.rabbitmq.com/docs/backup)

安装包与校验文件随 [GitHub Release](https://github.com/LuYifei-TOS-Apps/tos-rabbitmq/releases) 提供。RabbitMQ 遵循 [MPL 2.0](https://github.com/rabbitmq/rabbitmq-server/blob/v4.4.1/LICENSE)。
