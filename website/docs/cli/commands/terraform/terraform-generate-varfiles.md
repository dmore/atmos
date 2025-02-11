---
title: atmos terraform generate varfiles
sidebar_label: generate varfiles
sidebar_class_name: command
id: generate-varfiles
description: Use this command to generate the Terraform varfiles (`.tfvar`) for all Atmos terraform components in all stacks.
---

:::note Purpose
Use this command to generate the Terraform varfiles (`.tfvar`) for all Atmos terraform [components](/core-concepts/components) in
all [stacks](/core-concepts/stacks).
:::

## Usage

Executes `terraform generate varfiles` command.

```shell
atmos terraform generate varfiles [options]
```

This command generates varfiles for all Atmos terraform components in all stacks.

:::tip
Run `atmos terraform generate varfiles --help` to see all the available options
:::

## Examples

```shell
atmos terraform generate varfiles --file-template {component-path}/{environment}-{stage}.tfvars.json
atmos terraform generate varfiles --file-template /configs/{tenant}/{environment}/{stage}/{component}.json
atmos terraform generate varfiles --file-template /{tenant}/{stage}/{region}/{component}.yaml
atmos terraform generate varfiles --stacks orgs/cp/tenant1/staging/us-east-2,orgs/cp/tenant2/dev/us-east-2
atmos terraform generate varfiles --stacks tenant1-ue2-staging,tenant1-ue2-prod
atmos terraform generate varfiles --stacks orgs/cp/tenant1/staging/us-east-2,tenant1-ue2-prod
atmos terraform generate varfiles --components <component1>,<component2> --file-template <file_template>
atmos terraform generate varfiles --format hcl --file-template <file_template>
atmos terraform generate varfiles --format json --file-template <file_template>
atmos terraform generate varfiles --format yaml --file-template <file_template>
```

## Flags

| Flag              | Description                                                                                                                                                                                                                                                                                                                   | Alias | Required |
|:------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------|:---------|
| `--file-template` | Varfile template (path, file name, and file extension).<br/>Supports absolute and relative paths.<br/>Supports context tokens: `{namespace}`, `{tenant}`, `{environment}`,<br/>`{region}`, `{stage}`, `{base-component}`, `{component}`, `{component-path}`.<br/>All subdirectories in the path will be created automatically |       | yes      |
| `--stacks`        | Only process the specified stacks (comma-separated values).<br/>The names of top-level stack config files and Atmos stack names are supported                                                                                                                                                                                 |       | no       |
| `--components`    | Generate varfiles only for the specified Atmos components<br/>(comma-separated values)                                                                                                                                                                                                                                        |       | no       |
| `--format`        | Varfile format: `hcl`, `json`, `yaml` (`json` is default)                                                                                                                                                                                                                                                                     |       | no       |
| `--dry-run`       | Dry run                                                                                                                                                                                                                                                                                                                       |       | no       |
