## ✅ Step 1: Create the `argocd` namespace

```bash
kubectl create namespace argocd
```

---

## ✅ Step 2: Install Argo CD (Official YAML)

```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

## ✅ Step 3: Expose the Argo CD UI

By default, Argo CD API server is a **ClusterIP** (internal only). You have three options:

### Port Forward (recommended for local/dev)

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

Then open:
➡️ [http://localhost:8080](http://localhost:8080)

## ✅ Step 4: Get Argo CD Admin Password

```bash
kubectl get secret argocd-initial-admin-secret -n argocd \
  -o jsonpath="{.data.password}" | base64 -d
```

Use:

* **Username:** `admin`
* **Password:** (from above command)
