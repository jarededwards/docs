---
title: Install
---

# Civo Platform Installation

`kubefirst` is our command line tool that installs a fully automated platform of open source cloud native tools to your Civo cloud with a simple command.

![kubefirst Civo with GitLab Cluster Diagram](../../../img/civo/gitlab/installation-diagram-light.png#light-mode)![kubefirst Civo with GitLab Cluster Diagram](../../../img/civo/gitlab/installation-diagram-dark.png#dark-mode)

## Prerequisites

[Install](../../../kubefirst/overview.md#install-the-kubefirst-cli) the kubefirst CLI.

### GitLab

- Create or use an existing [GitLab account](https://gitlab.com).
- Create a [GitLab group](https://docs.gitlab.com/ee/user/group/) developer permissions.

> GitLab SaaS offering has limitations that require us to use groups contrary to GitHub which can be use without an organization.

### Civo

For kubefirst to be able to provision your Civo cloud resources:

- A [Civo account](https://dashboard.civo.com/signup) in which you are an account owner.
- A publicly routable [DNS](https://www.civo.com/learn/configure-dns#adding-a-domain-name).
- A [Civo token](https://dashboard.civo.com/security).

## Create your new kubefirst cluster

Adjust the following command with your GitHub and Civo tokens in addition to the appropriate values for your new platform.

```shell
export GITLAB_TOKEN=xxxxxxxxxxxxxxxx
export CIVO_TOKEN=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

kubefirst civo create \
  --alerts-email yourdistro@your-company.io \
  --git-provider gitlab \
  --gitlab-group your-gitlab-group \
  --domain-name your-domain.io \
  --cluster-name kubefirst
```

The kubefirst cli will produce a directory of utilities, a state file, and some staged platform content that can now be found in the `~/.kubefirst` and `~/.k1` folders on your local machine.

After the ~10 minute installation, your browser will launch a new tab to the [kubefirst Console](https://github.com/kubefirst/console), which will help you navigate your new suite of tools running in your new Civo cluster.

If your deployment is not successful, errors and troubleshooting information will be stored in a local log file specified during the installation run.

## Example of terminal output following cluster creation

![terminal handoff](../../../img/civo/gitlab/handoff-screen.png)

## Root credentials

To obtain your 3 initial passwords, run

```bash
kubefirst civo root-credentials
```

![terminal handoff](../../../img/common/kubefirst/root-credentials.png)

:::note the `kubefirst civo root-credentials` command was introduced in 2.0.1

## Connecting to Kubernetes

To connect to your new Kubernetes cluster, run

```bash
export KUBECONFIG=~/.k1/kubeconfig
```

To view all cluster pods, run

```bash
kubectl get pods -A
```

### Installed Applications

To see what is installed by kubefirst, check the [overview page](../../overview.md#platforms-details).
