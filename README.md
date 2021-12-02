# Grafana Tokio Console Data Source

This is a Grafana data source which can connect to the Tokio [`console`] subscriber. It provides similar functionality to the `console` [TUI frontend][console-frontend].

## Getting started

### Running Grafana locally

You'll need to clone Grafana and run a specific branch to get some nice extra things working:

1. Clone Grafana

   ```bash
   git clone git@github.com/grafana/grafana
   ```

2. Check out the custom branch

   ```bash
   git checkout table-charts-with-convert-to-json
   ```

3. Build the frontend

   ```bash
   yarn && yarn dev
   ```

   or, to watch for changes

   ```bash
   yarn && yarn watch
   ```

4. Change some config - make sure to change the 'plugins' path to the parent directory of this
   repo.

   ```bash
   cat <<EOF > conf/custom.ini
   app_mode = development
   [log]
   level = debug

   [paths]
   plugins = /Users/ben/repos/grafana-plugins  # or wherever you cloned this repo
   
   [plugins]
   allow_loading_unsigned_plugins = grafana-tokio-console-app
   plugin_admin_enabled = true
   ```

5. Run the Grafana backend

   ```bash
   make run
   ```

### Plugin frontend

At the repository root:

1. Install dependencies

   ```bash
   yarn install
   ```

2. Build plugin in development mode or run in watch mode

   ```bash
   yarn dev
   ```

   or

   ```bash
   yarn watch
   ```

3. Build plugin in production mode

   ```bash
   yarn build
   ```

### Plugin backend

Make sure you have a recent version of Rust (run `rustup update stable`), and install [`cargo-watch`].

Then, in the `backend` directory:

```bash
cargo xtask watch
```

[`console`]: https://github.com/tokio-rs/console
[console-frontend]: https://github.com/tokio-rs/console#extremely-cool-and-amazing-screenshots
[`cargo-watch`]: https://github.com/watchexec/cargo-watch/
