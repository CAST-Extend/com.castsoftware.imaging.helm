-------------------------------------------------------------------------------------------------------------
Package chart:
helm package charts\imaging\ -d docs
helm repo index docs/ --url https://CAST-Extend.github.io/com.castsoftware.imaging.helm/

Adding/Updating New Charts:
When you want to add new charts or update existing ones:
1. Add/update charts in the charts/ directory
2. Package the updated charts:
    helm package .\charts\imaging-323\ -d docs
    helm package .\charts\imaging-330\ -d docs
3. Update the index:
    helm repo index docs/ --url https://CAST-Extend.github.io/com.castsoftware.imaging.helm/ --merge docs/index.yaml
4. Commit and push:
    git add .
    git commit -m "Update charts"
    git push origin main

*****************************
Users repo commands examples:
*****************************
$ helm repo add castimaging https://CAST-Extend.github.io/com.castsoftware.imaging.helm/
$ helm repo update

$ helm repo ls
NAME        URL
gitlab      https://charts.gitlab.io
castimaging https://CAST-Extend.github.io/com.castsoftware.imaging.helm/

$ helm search repo castimaging
NAME                CHART VERSION   APP VERSION     DESCRIPTION
castimaging/imaging 3.3.0           3.3.0           A Helm chart for Kubernetes

$ helm search repo castimaging --versions
NAME                    CHART VERSION   APP VERSION     DESCRIPTION
castimaging/imaging     3.3.0           3.3.0           A Helm chart for Kubernetes
castimaging/imaging     3.2.3           3.2.3           A Helm chart for Kubernetes

Retrieve and customize values.yaml:
$ helm show values castimaging/imaging > my-values.yaml
Install :
$ helm install imaging-330 --create-namespace --namespace castimaging -f my-values.yaml --version 3.3.0 castimaging/imaging

-------------------------------------------------------------------------------------------------------------
