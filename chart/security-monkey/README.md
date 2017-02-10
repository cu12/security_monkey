# Security Monkey

[Security Monkey](https://github.com/Netflix/security_monkey) monitors policy changes and alerts on insecure configurations in an AWS account.

## Introduction

This chart bootstraps a Security Monkey deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager. The chart is meant to be used on a cluster running in AWS.

## Prerequisites

- Kubernetes 1.4+ with Beta APIs enabled

## Installing the Chart

To install the chart with the release name `my-release`:

```bash
$ helm install --name my-release ./secmonkey
```

The command deploys Security Monkey on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

By default a random password will be generated for the `security_monkey_postgres_user` user. If you'd like to set your own password change the `security_monkey_postgres_password` in the values.yaml.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```bash
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Security Monkey chart and their default values.

| Parameter                           | Description                         | Default                                                    |
| ----------------------------------- | ----------------------------------- | ---------------------------------------------------------- |
| `imageTag`                          | `mysql` image tag                   | `v0.8.0`                                                   |
| `imagePullPolicy`                   | Image pull policy                   | `Always` if `imageTag` is `latest`, else `IfNotPresent`    |
| `security_monkey_fqdn`              | FQDN for the service frontend       | `nil`                                                      |
| `aws_access_key_id`                 | Access key id for the IAM role      | `nil`                                                      |
| `aws_secret_access_key`             | Secret access key for the IAM role  | `nil`                                                      |
| `aws_rds_endpoint`                  | Address of the RDS instance         | `nil`                                                      |
| `security_monkey_postgres_user`     | Username for the database           | `security_monkey`                                          |
| `security_monkey_postgres_password` | Password for the database           | `nil`                                                      |
| `(api|scheduler).repository`        | Docker repo for the image           | `seayou/security_monkey-api`                               |
| `web.repository`                    | Docker repo for the image           | `seayou/security_monkey-nginx`                             |
| `api.resources`                     | CPU/Memory resource requests/limits | Memory: `512Mi`, CPU: `100m`                               |
| `(scheduler|web).resources`         | CPU/Memory resource requests/limits | Memory: `128Mi`, CPU: `100m`                               |

