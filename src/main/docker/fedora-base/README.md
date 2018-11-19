This dockerfile create a Fedora image with only the packages required for an Ansible target.

Since these instances will only be used for integration tests it's safe to embed the SSH key
like this. Anything more than an ephemeral instance should keep root's authorized keys in a
volume.

The SSH keypair was generated with

```{bash}
ssh-keygen -t rsa -b 2048
```

