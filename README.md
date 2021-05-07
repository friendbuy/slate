# FBOT Merchant API (MAPI) Documentation

Friendbuy uses the [Slate](https://github.com/slatedocs/slate/wiki) framework for maintaining our API documentation. Read the [Getting Started section of the Slate wiki](https://github.com/slatedocs/slate/wiki#getting-started) to learn how to use Slate or the upstream [README.md](https://github.com/slatedocs/slate/blob/main/README.md) for more information. This repo is cloned from [https://github.com/slatedocs/slate].

The MAPI API specification that this documentation describes is maintained in OpenAPI format in the [fbt-api-docs](https://github.com/friendbuy/fbt-api-docs) repo, so this documentation needs to be updated when fbt-api-docs'd API definition is changed. The [widdershins](https://github.com/Mermade/widdershins) documentation generator _may_ be useful in generating (parts) of this documentation from the OpenAPI-format spec but is not necessary for small updates.

## Getting Started with Slate

### Prerequisites

You're going to need:

- **Linux or macOS** — Windows may work, but is unsupported.
- **Ruby, version 2.3.1 or newer**
- **Bundler** — If Ruby is already installed, but the `bundle` command doesn't work, just run `gem install bundler` in a terminal.

### Getting Set Up

1. Clone this repo to your machine with `git clone git@github.com:friendbuy/slate.git`.
2. `cd slate`
3. Initialize and start Slate. You can either do this locally, or with Vagrant:

```shell
# either run this to run locally
bundle install
bundle exec middleman server

# OR run this to run with vagrant
vagrant up
```

You can now see the docs at http://localhost:4567. Whoa! That was fast!

### Build And Deploy

1. Build files to `build` folder

```shell
bundle exec middleman build --clean --no-parallel
```

2. Deploy

Login to the AWS console and upload files in the build folder to the root of:  
`https://console.aws.amazon.com/s3/buckets/developers.fbot.me/?region=us-east-1`

Make sure all files are uploaded with object read permission enabled for everybody.

Create a Cloudfront invalidation for developers.friendbuy.io distribution.

You can view the docs at:

- Production: https://developers.friendbuy.io/
- Sandbox: https://developers.fbot-sandbox.me/

Now that Slate is all set up on your machine, you'll probably want to learn more about [editing Slate markdown](https://github.com/slatedocs/slate/wiki/Markdown-Syntax), or [how to publish your docs](https://github.com/slatedocs/slate/wiki/Deploying-Slate).

If you'd prefer to use Docker, instructions are available [in the wiki](https://github.com/slatedocs/slate/wiki/Docker).

### Note on JavaScript Runtime

For those who don't have JavaScript runtime or are experiencing JavaScript runtime issues with ExecJS, it is recommended to add the [rubyracer gem](https://github.com/cowboyd/therubyracer) to your gemfile and run `bundle` again.

### Note on Widdershins

How to run widdershins:

``` shell
# Install widdershins globally.
npm install -g widdershins

widdershins -o source/includes/_api_docs.md ../fbt-api-docs/build/v1/openapi.yaml
```

