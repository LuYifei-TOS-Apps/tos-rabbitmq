# RabbitMQ on TOS privacy policy

This policy covers the self-hosted TOS package for RabbitMQ. The NAS administrator operates the installation and controls its data and backups.

## Data and purpose

RabbitMQ handles message bodies, routing metadata, topology, and user or permission settings. Durable messages and node state can persist on the NAS under `/var/lib/rabbitmq`. This directory also holds the generated initial credential.

## Sharing and external services

RabbitMQ delivers messages to authorized clients and services according to the configured queues, exchanges and permissions. Optional federation or forwarding, if configured, can send messages to operator-selected brokers.

Installation and updates can contact TOS distribution services and container registries to obtain packages and images. Requests to external services are handled according to the services and locations selected by the operator.

## Retention, access, correction and deletion

Messages are kept until acknowledged, expired, purged or deleted according to the queue configuration. Authorized administrators can inspect and change topology and users in the management UI, and purge or delete queues when appropriate. Producers can publish corrected data.

To remove an entire instance, stop it and identify the app-owned storage in Docker Manager before deleting it. The NAS administrator should handle retained backups separately and verify the effects of the TOS uninstall options. Contact the NAS administrator to request access, correction or deletion of data held by the instance.

## Security and support

Restrict AMQP and management ports, protect the generated credential and state directory, and enable TLS for clients across trust boundaries.

For questions about the TOS package, use the repository's issue tracker. Omit private data, credentials and unredacted logs from public reports.
