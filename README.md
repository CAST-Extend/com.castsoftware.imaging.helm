# Documentation

This project is used to host the CAST Imaging helm repository

## Examples of repo user commands 
- Add repo
```
helm repo add castimaging https://CAST-Extend.github.io/com.castsoftware.imaging.helm/
helm repo update
```

- List repos
```
helm repo ls
NAME        URL
gitlab      https://charts.gitlab.io
castimaging https://CAST-Extend.github.io/com.castsoftware.imaging.helm/
```

- Get repo content
```
helm search repo castimaging
NAME                CHART VERSION   APP VERSION     DESCRIPTION
castimaging/imaging 3.3.0           3.3.0           A Helm chart for Kubernetes
```

- Get repo content with versions available
```
helm search repo castimaging --versions
NAME                    CHART VERSION   APP VERSION     DESCRIPTION
castimaging/imaging     3.3.0           3.3.0           A Helm chart for Kubernetes
castimaging/imaging     3.2.3           3.2.3           A Helm chart for Kubernetes
```

- Retrieve and customize values.yaml
```
helm show values castimaging/imaging > my-values.yaml
```

- Install / Upgrade
```
helm install castimaging --create-namespace --namespace castimaging -f values323-eks-priv.yaml --version 3.2.3 castimaging/imaging
helm install castimaging --create-namespace --namespace castimaging -f values330-eks-priv.yaml --version 3.3.0 castimaging/imaging
helm upgrade castimaging                    --namespace castimaging -f values330-eks-priv.yaml --version 3.3.0 castimaging/imaging
```


## Admin commands (for repo mngr)

- Package chart creation
```
helm package charts\imaging\ -d docs
helm repo index docs/ --url https://CAST-Extend.github.io/com.castsoftware.imaging.helm/
```

- Adding/Updating Charts
When you want to add new charts or update existing ones:
1. Add/update charts in the charts/ directory
2. Package the updated charts:
    ```
    helm package .\charts\imaging-323\ -d docs
    helm package .\charts\imaging-331\ -d docs
    helm package .\charts\imaging-340\ -d docs
    helm package .\charts\imaging-341\ -d docs
    helm package .\charts\imaging-342\ -d docs
    helm package .\charts\imaging-344\ -d docs
    helm package .\charts\imaging-345\ -d docs
    helm package .\charts\imaging-350\ -d docs
    helm package .\charts\imaging-353\ -d docs
    ```
3. Update the index:
    ```
    helm repo index docs/ --url https://CAST-Extend.github.io/com.castsoftware.imaging.helm/ --merge docs/index.yaml
    ```
4. Commit and push