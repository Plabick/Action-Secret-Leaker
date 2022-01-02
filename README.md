# GitHub Secret Extractor
[![Unit Tests](https://github.com/Plabick/GitHub-Secret-Extractor/actions/workflows/test.yml/badge.svg?event=push)](https://github.com/Plabick/GitHub-Secret-Extractor/actions/workflows/test.yml)

A simple tool to extract the plain text values of [GitHub Secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets). This action was made to show the importance of limiting who can run workflows in repositories with secrets. 

This action takes a string, `secret` as input and prints an encoded version of it to the console. You can then use [this tool](https://plabick.github.io/Actions-Secret-Decoder/) to get the secret in plain text. 
### Usage
```yaml
    - name: Extract A Juicy Secret
      uses: Plabick/GitHub-Secret-Extractor@master
      with:
        secret: ${{ secrets.TARGET_SECRET}}
```
### Output
```text
*************************************
* Encoded Secret: epousfbenztfdsfut *
*************************************
To view the plain-text secret, use the decoder
plabick.github.io/Actions-Secret-Decoder/
```
## Why is the output encoded?
GitHub redacts text that matches secrets from the console. The only way to output secrets in the console is to encode them. 

## How can I protect my secrets?

To protect your secrets from a variant of this tool that uses an arbitrary encoding scheme, limit who can modify workflows on repos with secrets. There is no other way to prevent the disclosure of stored secrets. 
