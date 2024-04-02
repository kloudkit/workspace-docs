---
outline: deep
---

# Extra Features

It would be impossible to pre-install and configuring every possible package or feature,
while maintain a flexible *workspace* footprint.
Therefore, we developed an *opt-in* method to seamlessly install and configure additional
features at the user's discretion.

Behind the scenes, we are simply running an *Ansible playbook* in order to install the
desired feature.

## Installing Features

We provide two methods for installing additional features in the *workspace*.
You can choose the method that best fits your needs.

### Install at Boot

Upon workspace startup, we evaluate the value of the `WS_EXTRA_FEATURES` environment
variable in order to automate the installation of additional *features*.

```sh{2}
docker run \
  -e WS_EXTRA_FEATURES="dotnet jupyter" \
  ghcr.io/kloudkit/workspace:latest
```

### Manual Installation

Manual installing features is as easy as running a simple command line prompt.

```sh
# Help information
ws feature install -h

# Example: installing PHP
ws feature install php
```

As mentioned above, all features are backed by Ansible playbooks.
All playbooks are stored in the `/features` root directory.

The directory location can be overridden using the `--root` flag when installing:

```sh
ws feature install php --root /alternate
```

## Available Features

::: info
Have in mind a feature we didn't think about yet?

Feel free to make submit a suggestion or actively contribute the feature yourself.
For more information, visit our [contribution guide](/contribute/).
:::

| Feature   | Description                             |
| --------- | --------------------------------------- |
| `dotnet`  | dagger.io CLI and SDK                   |
| `dagger`  | Jupyter packages and related extensions |
| `jupyter` | .NET framework and related extensions   |
| `php`     | PHP and related extensions              |
