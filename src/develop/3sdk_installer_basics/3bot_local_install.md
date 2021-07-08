
## Install a 3Bot on your local machine

### Quick Start with js-sdk

#### System requirements for installation on the host

- Ubuntu 18.04 or higher, MacOS 10.9 or higher
- Windows 10, version 2004 could run using [wsl2](https://docs.microsoft.com/en-us/windows/wsl/wsl2-index) using ubuntu 20.04 or later
- The SDK uses [python3](https://python.org), python3-pip, [git](https://git-scm.com), poetry, [nginx](https://www.nginx.com), [redis](https://redis.io), [mkcert](https://github.com/FiloSottile/mkcert) is needed to trust the self signed certificates when used in local development environment.
- Browser (we recommend using Google chrome)

##### Mac OSX

For Mac OSX 

Install packages (git, nginx, redis, tmux, python3, mkcert) on MacOS
 ```
 brew install nginx redis tmux git python3 mkcert
 ```


##### Ubuntu

For GNU/Linux Ubuntu systems
 ```
 apt-get update
 apt-get install -y git python3-venv python3-pip redis-server tmux nginx;
 pip3 install poetry
 ```
 
#### Installing the js-sdk

After having the [requirements](https://github.com/Threefoldtech/js-sdk/blob/development/docs/wiki/quick_start.md#system-requirements-for-installation-on-the-host) installed on your system 

##### Installation using pip (don't use yet until we have an official release)

Just doing `python3 -m pip install js-sdk` is enough

##### Installation for experts or developers

- Make sure to have the [requirements](https://github.com/Threefoldtech/js-sdk/blob/development/docs/wiki/quick_start.md#system-requirements-for-installation-on-the-host) installed 
This version of the SDK tries to be isolated as possible in case of developers or the endusers, and we are achieving that level of isolation using poetry for the whole development/publishing process

- To install poetry `pip3 install poetry` or from [here](https://python-poetry.org/docs/#installation)
- Clone the repository `git clone https://github.com/Threefoldtech/js-sdk`
- Prepare the environment and the python dependencies

 ```bash
 cd js-sdk
 poetry update
 poetry install
 poetry shell
 ```

#### Running your 3Bot

##### using mkcert

[mkcert](https://github.com/FiloSottile/mkcert) is optionally needed to trust the self signed certificates when used in local development environment. All you need to do is install it in your system under the name `mkcert` and do `mkcert -install`

After the installation steps you should have an executable `threebot`

- in case of pip it should be available for the user
- in case of poetry you need to be in the isolated environment using `poetry shell`

3Bot server could run using `threebot start --local` starts a server on `8443, 8080`. If you want to use `80, 443` ports you need to set [capabilities](3bot_running) for nginx binary (in case of linux) or install as root in case of OSX.

 ```bash
 threebot start --local
 ```

- After installing the sdk successfully, when starting 3Bot server using the following commands, you will be prompted to enter the required information to setup an initial default identity which includes the explorer url to be used

- Then it will start 3Bot server you will see some thing like that

 ![configure](img/identity_new.png)

- After success you could visit the admin dashboard at https://localhost:8443/admin and start creating reservations

 ![configure](img/success.png)

#### Cleaning up Data from previous installations

- Data is stored in `~/.config/jumpscale/secureconfig/jumpscale`. if you want to start over, you can remove that directory using `rm ~/.config/jumpscale/secureconfig/jumpscale`
- There're also some configurations that gets generated e.g (nginx configurations), logs and binaries when copied in `~/sandbox` directory 
