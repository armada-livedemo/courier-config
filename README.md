# Courier-config
This config fetches configuration for players-backend from project repository (dev config) and 'secret' repository (aws config).

## How to run
Assuming you're in players-backend vagrant run:

- `sudo cp -r /projects/courier-config /etc/opt/` to copy courier configuration to configurations directory.
- `armada run courier --env production-office` to run courier.

Once courier is running, it should automatically fetch configurations from git repos. Now, if you run new players-backend service it will automatically mount it and `hermes` will pick it up.

Notice that if you have a running `players-backend` service, `armada restart` won't add courier configuration because it requires a change (mounting a volume) in run parameters. 
Once configuration is loaded, it will be automatically reloaded every time it changes without a need to restart a service.