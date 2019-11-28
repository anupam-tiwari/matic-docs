### Install GO & DEP

Install go by following the [official docs](https://golang.org/doc/install). Remember to set your `$GOPATH`, `$GOBIN`, and `$PATH` environment variables, for example:

```js
$ mkdir -p $HOME/go/bin
$ echo "export GOPATH=$HOME/go" >> ~/.bash_profile
$ source ~/.bash_profile
$ echo "export GOBIN=$GOPATH/bin" >> ~/.bash_profile
$ source ~/.bash_profile
$ echo "export PATH=$PATH:$GOBIN" >> ~/.bash_profile
$ source ~/.bash_profile

```

Or we have a script to install go for you

```js

$ curl https://gist.githubusercontent.com/vaibhavchellani/cbe0fa947dc0a6557cb9583d081ff8ce/raw/d47b3df14ccffdd7a965e44c39fb5ec235360166/new.sh > install_go.sh
$ bash install_go.sh

```

> Note: Go version 1.11+ is recommended

### Install DEP

Steps to install DEP are [here](https://golang.github.io/dep/docs/installation.html)

### Install RabbitMq

A helper service called `bridge` which is embedded into heimdall codebase requires `rabbit-mq` to queue transactions to multiple networks. Installing it should be pretty straightforward. Checkout the download instructions [here](https://www.rabbitmq.com/download.html).

```js

$ rabbitmq-server

```

This will run the `rabbitmq` server

### Install make

You need to install `make` to run some commands. Using the below commands you can install `make` depending on your system.

**For Ubuntu**

```
$ sudo apt-get install build-essential
```

**For MacOS**

```
$ brew install make
```

### Install Heimdall

Next, let's install the latest version of Heimdall. Here, we'll use the master branch, which contains the latest stable release. If necessary, make sure you `git checkout` the correct [released version](https://github.com/maticnetwork/heimdall/releases)

```js
$ mkdir -p $GOPATH/src/github.com/maticnetwork
$ cd $GOPATH/src/github.com/maticnetwork
$ git clone https://github.com/maticnetwork/heimdall
$ cd heimdall && git checkout master
$ make dep && make install
```

That will install the `heimdalld` and `heimdallcli` binaries. Verify that everything is OK:

```js

$ heimdalld --help

```

### Setting up a new node

```js

$ heimdalld init

```

This will emit the following output which shows your node id and chain id, these can be changed before starting a chain from the genesis file.

```js

{
  "chain_id": "heimdall-pldzov",
  "node_id": "ae8fd49c192f39a400c00b328d4fd109d5bcb71d"
}

```