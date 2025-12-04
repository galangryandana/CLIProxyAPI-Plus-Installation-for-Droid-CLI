Step-by-step installation (English)

1) Clone the repository:
```
cd ~/{any-directory}
git clone --depth 1 https://github.com/router-for-me/CLIProxyAPIPlus.git
cd CLIProxyAPIPlus
```

2) Build the binary (requires Go):
```
go build -o cliproxyapi-plus ./cmd/server
```

3) Install the binary, then verify `--help` shows the `--github-copilot-login` option:
```
sudo mv cliproxyapi-plus /usr/local/bin/
cliproxyapi-plus --help
```

4) Remove the clone when finished:
```
cd ~/{any-directory}
rm -rf CLIProxyAPIPlus
```

5) Create the config directory and base config:
```
mkdir -p ~/.cli-proxy-api

cat > ~/.cli-proxy-api/config.yaml << 'EOF'
port: 8317
auth-dir: "~/.cli-proxy-api"
api-keys:
  - "sk-dummy"
quota-exceeded:
  switch-project: true
  switch-preview-model: true
EOF
```

6) Configure the custom model droid in `config.json` (included in this repo).

7) Collect OAuth login data for each provider:
```
cliproxyapi-plus --config ~/.cli-proxy-api/config.yaml --github-copilot-login
cliproxyapi-plus --config ~/.cli-proxy-api/config.yaml --codex-login
cliproxyapi-plus --config ~/.cli-proxy-api/config.yaml --antigravity-login
cliproxyapi-plus --config ~/.cli-proxy-api/config.yaml --claude-login
cliproxyapi-plus --config ~/.cli-proxy-api/config.yaml --iflow-login
cliproxyapi-plus --config ~/.cli-proxy-api/config.yaml --login
cliproxyapi-plus --config ~/.cli-proxy-api/config.yaml --qwen-login
```

8) Start the server with logs:
```
cliproxyapi-plus --config ~/.cli-proxy-api/config.yaml
```


## Credits
https://github.com/router-for-me/CLIProxyAPI
https://github.com/router-for-me/CLIProxyAPIPlus
