![Logo](https://framerusercontent.com/images/dGhFEb4pIwUJ5SArbs7udVlSs.png)
<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-1-orange.svg?style=flat-square)](#contributors-)
<!-- ALL-CONTRIBUTORS-BADGE:END -->


# Giza Command Line Interface
```text
  _______  __   ________      ___           ______  __       __
 /  _____||  | |       /     /   \         /      ||  |     |  |
|  |  __  |  | `---/  /     /  ^  \       |  ,----'|  |     |  |
|  | |_ | |  |    /  /     /  /_\  \      |  |     |  |     |  |
|  |__| | |  |   /  /----./  _____  \     |  `----.|  `----.|  |
 \______| |__|  /________/__/     \__\     \______||_______||__|

```

Welcome to Giza`s Platform CLI!

This CLI provides the utilities to interact with Giza Platform using the terminal.


## Installation

Clone the repository and install it with `pip`:

```bash
    git clone git@github.com:gizatechxyz/giza-cli.git
    cd giza-cli
    pip install .
```

Or install it directly from the repo:
```bash
  pip install git+ssh://git@github.com/gizatechxyz/giza-cli.git
```


## Usage/Examples

### Create User

This is the first step! We create the user and then we need to verify the account by checking the email.

```console
> giza users create

Enter your username 😎: my-username
Enter your password 🥷 : (this is a secret)
Enter your email 📧: gonzalo@gizatech.xyz
[giza][2023-06-23 12:29:40.543] Creating user in Giza Platform ✅
{'email': 'gonzalo@gizatech.xyz', 'username': 'my-username', 'is_active': False}
[giza][2023-06-23 12:29:41.417] User created ✅. Check for a verification email 📧
```

### Login

If it is not verified login will be disabled!

```console
> giza users login

Enter your username 😎: my-username
Enter your password 🥷 :
[giza][2023-06-23 12:32:17.917] Log into Giza Platform
[giza][2023-06-23 12:32:18.716] ⛔️Could not authorize the user⛔️
[giza][2023-06-23 12:32:18.718] ⛔️Status code -> 400⛔️
[giza][2023-06-23 12:32:18.719] ⛔️Error message -> {'detail': 'Inactive user'}⛔️
```

But once we verify the account we will be able to authenticate with the platform.

```console
> giza users login

Enter your username 😎: my-username
Enter your password 🥷 :
[giza][2023-06-23 12:34:33.576] Log into Giza Platform
[giza][2023-06-23 12:34:34.400] Successfully logged into Giza Platform ✅
```

### Retrieve user information

Now that we are authenticated we can connect with the platform!

```console
> giza users me

[giza][2023-06-23 12:35:33.287] Retrieving information about me!
{
  "username": "my-username",
  "email": "gonzalo@gizatech.xyz",
  "is_active": true
}
```

### Transpile a model!

We have our `onnx` model and we want to transpile it, `giza` makes it easy by providing the command for it!

```console
> giza transpile MNIST_quant.onnx --output-path my_awesome_model

[giza][2023-06-23 12:39:01.587] Reading model from path: MNIST_quant.onnx
[giza][2023-06-23 12:39:01.588] Sending model for transpilation
[giza][2023-06-23 12:39:04.657] Transpilation recieved!✅
[giza][2023-06-23 12:39:04.670] Trasnpilation saved at: my_awesome_model
```

Let's check the result:

```console
> tree my_awesome_model

my_awesome_model
├── cairo_project.cairo
├── scarb.toml
└── src
    ├── conv1
    │   └── Conv_quant.cairo
    ├── conv1.cairo
    ├── conv2
    │   └── Conv_quant.cairo
    ├── conv2.cairo
    ├── fc1
    │   └── Gemm_MatMul_quant.cairo
    ├── fc1.cairo
    ├── fc2
    │   └── Gemm_MatMul_quant.cairo
    ├── fc2.cairo
    ├── graph.cairo
    └── lib.cairo
```

## Contributors ✨

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tbody>
    <tr>
      <td align="center" valign="top" width="14.28%"><a href="https://es.linkedin.com/in/gonzalo-mellizo-soto-diaz-590260108"><img src="https://avatars.githubusercontent.com/u/18899187?v=4?s=100" width="100px;" alt="Gonzalo Mellizo"/><br /><sub><b>Gonzalo Mellizo</b></sub></a><br /><a href="https://github.com/gizatechxyz/giza-cli/commits?author=Gonmeso" title="Code">💻</a></td>
    </tr>
  </tbody>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!