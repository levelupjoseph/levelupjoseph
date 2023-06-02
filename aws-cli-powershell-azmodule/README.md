# Dependencies
# ansible core
# pip install ansible-navigator

podman
git

1. Build a new container
```
ansible-builder build --container-runtime podman -t ruffin/ansible-aws-powershell-az-module:latest
# quay.io/davidruffin/amt/ansible-aws-powershell-az-module
# quay.io/ruffin/ansible-aws-powershell-az-module 
````

2. Login to container to test
```
podman run -it ruffin/ansible-aws-powershell-az-module:latest /bin/bash
```

2. login to quay and redhat
```
podman login quay.io
podman login registry.redhat.io
```

3. tag container
```
podman tag ruffin/ansible-aws-powershell-az-module:latest quay.io/ruffin/ansible-aws-powershell-az-module:latest
```

4. Push to quay
```
podman push quay.io/ruffin/ansible-aws-powershell-az-module:latest
```

5. Run playbook in execution environment
```
ansible-navigator run example_playbook.yml -i inventory.ini --eei quay.io/ruffin/ansible-aws-powershell-az-module:latest --mode stdout
```
