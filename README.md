# TFLint Ruleset Template

## Releasing

```shell
brew install goreleaser/tap/goreleaser gpg2 gnupg pinentry-mac

mkdir ~/.gnupg
chmod 700 ~/.gnupg

echo "pinentry-program $(brew --prefix)/bin/pinentry-mac" > ~/.gnupg/gpg-agent.conf
echo 'use-agent' > ~/.gnupg/gpg.conf
echo 'export GPG_TTY=$(tty)' >> ~/.zshrc
source ~/.zshrc

gpg --full-gen-key
gpg -K --keyid-format SHORT

# sec   rsa3072/85AA3AB7 2022-11-14 [SC]
#       F59422EA0CCFFFA7FA264CF3AB4B300B85AA3AB7
# 85AA3AB7 is your key-id
# F59422EA0C....A3AB7 is your fingerprint

export GPG_FINGERPRINT="{FINGERPRINT}"

goreleaser release
```

## Usage

You can install the plugin with `tflint --init`. Declare a config in `.tflint.hcl` as follows:

```text
plugin "template" {
  enabled = true

  version = "1.0.2"
  source = "github.com/christiansalway1/tflint-ruleset-template"

}
```
