# flox-agent-plugins

Custom agent plugins packaged with `flox-agent import` and published to the `mrdavidlaing-flox` FloxHub catalog for `aarch64-darwin`, `x86_64-linux`, and `aarch64-linux`.

## Setup (once)

Add a `FLOXHUB_TOKEN` secret to this repository (`Settings → Secrets and variables → Actions`) so the publish workflow can run `flox publish -o mrdavidlaing-flox`.

## Adding or updating a plugin

```bash
# Import a new plugin from GitHub
flox-agent import owner/repo

# Update an existing plugin to its latest commit
flox-agent import --replay prime-radiant-inc/toolsmith

# Stage and push — GitHub Actions builds and publishes all 3 architectures
git add .flox/
git commit -m "chore: update agent-plugin-toolsmith"
git push
```

Then install or upgrade in `mrdavidlaing-flox/agents`:

```bash
flox install -r mrdavidlaing-flox/agents mrdavidlaing-flox/agent-plugin-toolsmith
# in laingville:
./bin/upgrade-agents canary
./bin/upgrade-agents promote
```
