# gitea_actions_prometheus_exporter-project

The purpose of this repository is to provide a simple solution for testing the [Gitea Actions Prometheus Exporter](https://github.com/james9001/gitea_actions_prometheus_exporter)

## Setting up the environment

- Run `docker compose up` and wait for the containers to come up
- Navigate to http://localhost:3000, go to the bottom and click Install Gitea
- After it finishes installing, you'll see the login page - click "Register now" at the bottom. Set up a user account, this will become the global admin
- Check http://localhost:3000/-/admin/actions/runners as the act runner should be registered (just the one)
- From the Gitea GUI, create a remote for this repo and push to it
- You should now be able to use the workflow_dispatch GUI from the Actions tab of the remote repo to start a `fail-test.yaml` job
- Check the output: `curl http://localhost:9100/metrics`. When `fail-test.yaml` is finished, the counter metrics reporting failures will increment

## Developing

- `pre-commit install` to install hooks
- Install the Pip3 package `xmlformatter` i.e. `pip3 install xmlformatter --break-system-packages`
- Run this to exec all the pre-commit hooks on the entire project: `pre-commit run --all-files`
