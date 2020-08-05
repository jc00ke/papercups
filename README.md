# Papercups

Papercups is an open source live customer chat web app. We offer a hosted
version at [app.papercups.io](https://app.papercups.io/).

You can check out how our chat widget looks and play around with customizing it
on our [demo page](https://app.papercups.io/demo/). The chat widget component
is also open sourced at
[github.com/papercups-io/chat-widget](https://github.com/papercups-io/chat-widget).

_Watch how easy it is to get set up with our Slack integration 🚀 :_
![slack-setup](https://user-images.githubusercontent.com/4218509/88716918-a0583180-d0d4-11ea-93b3-12437ac51138.gif)

## One click Heroku deployment

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/papercups-io/papercups)

## Philosophy

We wanted to make a self-hosted version of tools like Intercom and Drift for
companies that have privacy and security concerns about having customer data
going to third party services. We’re starting with chat right now but we want
to expand into all forms of customer communication like email campaigns and
push notifications.

Stay tuned! We'll be posting a more detailed roadmap soon 🤓

## Getting started

Papercups runs on Elixir/Phoenix, with a TypeScript React app for the frontend.

- Install [PostgreSQL](https://wiki.postgresql.org/wiki/Detailed_installation_guides)
- Install [asdf](https://asdf-vm.com/#/core-manage-asdf-vm?id=install)
- Install [Erlang dependencies](https://github.com/asdf-vm/asdf-erlang#before-asdf-install)

```
git clone git@github.com:papercups-io/papercups.git
cd papercups
asdf install
mix local.hex
mix deps.get
cd assets && npm install
mix ecto.setup
mix phx.server
```

This will automatically start up the React frontend in watch mode on `localhost:3000`,
with the API running on `localhost:4000`.

The frontend code will start up automatically when you run `mix phx.server`,
but for more information see: [assets/README.md](assets/README.md)

### Developing on Docker

You can edit your local code when developing with docker and it will update in
the container.

_The docker file is made for development only at the moment_

```
docker build -t papercups . && docker-compose up
```

## Running tests

Create a PostgreSQL test database named: `chat_api_test`, and run:

```
mix test
```

## Get in touch

Come say hi to us on
[Slack](https://join.slack.com/t/papercups-io/shared_invite/zt-gfs0d269-dEHm3SYs_5KmFKQ9YhBzDw)
or [Discord](https://discord.gg/Dq2A3eh)! :wave:

# Appendix

(We'll add more instructions here as we implement more integrations.)

## Setting up email alerts

Set the environment variables in the
[`.env.example`](https://github.com/papercups-io/papercups/blob/master/.env.example) file.

At the moment we only support [Mailgun](https://www.mailgun.com/) — other
messaging channels are coming soon!

## Deploying

We currently use Heroku for deployments:

```
git push heroku master
heroku run "POOL_SIZE=2 mix ecto.migrate"
```

## Running compiler on file change

_Note_: Make sure you are running this inside of ChatApi otherwise it'll
trigger on UI changes

```
./scripts/compile_watch.sh
```

## Learn more about Phoenix

- Official website: https://www.phoenixframework.org/
- Guides: https://hexdocs.pm/phoenix/overview.html
- Docs: https://hexdocs.pm/phoenix
- Forum: https://elixirforum.com/c/phoenix-forum
- Source: https://github.com/phoenixframework/phoenix
