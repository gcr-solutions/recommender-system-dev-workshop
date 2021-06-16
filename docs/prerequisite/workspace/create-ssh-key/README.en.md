---
title: Create an SSH key
weight: 5
---

Please run this command to generate SSH Key in Cloud9. This key will be used on the worker node instances to allow ssh access if necessary.

```sh
ssh-keygen
```

{{% notice tip %}}
Press `enter` 3 times to take the default choices
{{% /notice %}}

Upload the public key to your EC2 region:

```sh
aws ec2 import-key-pair --key-name "gcr-rs-workshop-key" --public-key-material file://~/.ssh/id_rsa.pub