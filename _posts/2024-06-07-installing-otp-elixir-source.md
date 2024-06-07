---
layout: posts
title: "Installing OTP and Elixir from source code"
excerpt: "A reminder of the steps i need to remind myself each time i install/update these tools"
categories:
  - Elixir
tags:
  - OTP
  - Elixir
---

Erlang/OTP and Elixir are both available as pre-built binary packages by most OS package managers. However, lately I've noticed that most of these binary packages are releasing old versions from both of these languages. 
This guide will point out a couple of ways to fetch newer and still stable versions of both of these languages.

<figure>
    <a href="/assets/blog-images/natural_transformations.jpeg"><img src="/assets/blog-images/otp_elixir.png"></a>
</figure>

## OTP

We need to start installing OTP, which includes not only Erlang/OTP ecosystem but also the BEAM VM. We can fetch the code from OTP on any directory, in my case it's `~/opt`, where i leave all my deps that i need to compile before i install them.

> The complete building and installation instructions [can be found here](https://github.com/erlang/otp/blob/maint-27/HOWTO/INSTALL.md).

### Downloading and selecting the OTP version

We start by downloading the OTP repository from github

```
git clone https://github.com/erlang/otp
```

Checkout the branch or tag of your choice. Generally `maint-<version>` is recommended as these are the latest maintenance version.

```
git checkout maint-27    # current latest stable version
```

> If this isn't the first time installing OTP by source and you already have installed it this way, this is a good time to run the `make clean` command in order to cleanup any setup from the previous installation. This is to prevent unwanted errors on the building step.
### Configuring

Run the following commands to configure the build:

```
$ ./configure [ options ]
```


By default, Erlang/OTP release will be installed in `/usr/local/{bin,lib/erlang}`. If you for instance don't have the permission to install in the standard location, you can install Erlang/OTP somewhere else. For example, to install in `/opt/erlang/%OTP-VSN%/{bin,lib/erlang}`, use the `--prefix=/opt/erlang/%OTP-VSN%` option.

On some platforms Perl may behave strangely if certain locales are set. If you get errors when building, try setting the LANG variable:

```
$ export LANG=C   # Assuming bash/sh
```

### Building

Build the Erlang/OTP release.

```
$ make
```

### Testing

Before installation you should test whether your build is working properly by running our smoke test. The smoke test is a subset of the complete Erlang/OTP test suites. First you will need to build and release the test suites.

```
$ make release_tests
```

This creates an additional folder in `$ERL_TOP/release` called `tests`. Now, it's time to start the smoke test.

```
$ cd release/tests/test_server
$ $ERL_TOP/bin/erl -s ts install -s ts smoke_test batch -s init stop
```

To verify that everything is ok you should open `$ERL_TOP/release/tests/test_server/index.html` in your web browser and make sure that there are zero failed test cases.

> #### Note {: .info }
> 
> On builds without `crypto`, `ssl` and `ssh` there is a failed test case for undefined functions. Verify that the failed test case log only shows calls to skipped applications.

### Installing

You are now ready to install the Erlang/OTP release! The following command will install the release on your system.

```
$ make install
```

### Testing 

Once everything is installed, we can just run the `erl` command in order to enter the Erlang/OTP encironment.

## Installing Elixir

## Retrieve and compile Elixir

```shell
$ mkdir ~/dev
$ cd ~/dev
$ git clone https://github.com/elixir-lang/elixir.git
$ cd elixir 
$ make clean test
```

### Fetching ExDoc

Create a fork on GitHub at: [https://github.com/elixir-lang/ex_doc](https://github.com/elixir-lang/ex_doc)

Clone your fork:

```shell
$ cd ~/dev
$ git clone https://github.com/<github_username>/ex_doc
$ cd ex_doc
$ git remote add upstream https://github.com/elixir-lang/ex_doc
$ git fetch upstream
```

## Compile ExDoc

```shell
$ cd ~/dev/ex_doc && ../elixir/bin/mix do deps.get, compile
```

## How to use ExDoc for build documentation

For example, if we want to build Elixir documentation with ExDoc.

```shell
$ cd ~/dev/elixir
$ ../ex_doc/bin/ex_doc "Elixir" "1.16.2" "lib/elixir/ebin" -m "Kernel" -u "https://github.com/elixir-lang/elixir" -o doc -p http://elixir-lang.org/docs.html
```

The docs can be found below the `doc/` directory

