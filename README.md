# TFLint Ruleset Template

## Installation

TODO: This template repository does not contain release binaries, so this installation will not work. Please rewrite for your repository. See the "Building the plugin" section to get this template ruleset working.

You can install the plugin with `tflint --init`. Declare a config in `.tflint.hcl` as follows:

```hcl
plugin "template" {
  enabled = true

  version = "0.1.0"
  source  = "github.com/terraform-linters/tflint-ruleset-template"

  signing_key = <<-KEY
  -----BEGIN PGP PUBLIC KEY BLOCK-----
  mQINBGCqS2YBEADJ7gHktSV5NgUe08hD/uWWPwY07d5WZ1+F9I9SoiK/mtcNGz4P
  JLrYAIUTMBvrxk3I+kuwhp7MCk7CD/tRVkPRIklONgtKsp8jCke7FB3PuFlP/ptL
  SlbaXx53FCZSOzCJo9puZajVWydoGfnZi5apddd11Zw1FuJma3YElHZ1A1D2YvrF
  ...
  KEY
}
```

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

Create a `.tflint.hcl` file in the root of your repository with the following contents:

```text
plugin "template" {
  enabled = true

  version = "1.0.2"
  source = "github.com/christiansalway1/tflint-ruleset-template"

}
```
