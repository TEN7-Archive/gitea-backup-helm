# gitea-backup-helm

A helm chart to backup your Kubernetes-based Gitea instance to an S3 bucket or SFTP

## How it works

This chart provisions a cronjob which runs the [`ten7/gitea_backup`](https://hub.docker.com/repository/docker/ten7/gitea-backup) container. It uses the [`s3cmd`](https://s3tools.org) command to synchronize with one or more "remotes". Each remote can be either an S3 bucket, or an SFTP server.

## Features

* Synchronizes from multiple sources to multiple targets.
* Does not require persistent storage to function.
* Has no persistent container, or a cronjob.
* Supports multiple S3 and SFTP destinations.
* Can be installed multiple times in the same namespace, with different schedules, allowing you to make hourly/daily/weekly/monthly backups.

## Requirements

* Connection and credentials for source database servers.
* Connection and credentials for target S3 and/or SFTP providers.

## Installation

```shell
helm repo add gitea-backup https://ten7.github.io/gitea-backup-helm/
helm repo update
helm upgrade --install gitea-backup gitea-backup/gitea-backup --namespace=my-namespace -f path/to/my-values.yml
```

## Configuration

For a full list of values, see [values.yaml](https://raw.githubusercontent.com/ten7/gitea-backup-helm/main/charts/gitea-backup/values.yaml).

## License

MySQL Backup is licensed under GPLv3. See [LICENSE](https://raw.githubusercontent.com/ten7/gitea-backup-helm/main/LICENSE) for the complete language.
