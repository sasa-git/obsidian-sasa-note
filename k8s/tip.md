[k0sのk8sをk9sで見てみた](https://tech.drecom.co.jp/ac2020-k0sk8sk9s/)
k8sの学習用にオススメ

# 使用例
`kubectl get pods -n example12345`

`kubectl logs -n example12345 -f taurus-master-66786b67fb-ph77n`

contextの確認
`k config get-contexts`

contextの切り替え
`k config use-context docker-desktop`

# k8s dashboard

https://kubernetes.io/ja/docs/tasks/access-application-cluster/web-ui-dashboard/  
https://qiita.com/h-sakano/items/79bb15f7a0661e141c75

`kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0/aio/deploy/recommended.yaml`  
`kubectl -n kube-system get secret`  

```
$ kubectl -n kube-system get secret
deployment-controller-token-nn4ck                kubernetes.io/service-account-token   3      22h

$ kubectl -n kube-system describe secret deployment-controller-token-nn4ck
# token: が出てくるからコピペ
```

`kubectl proxy`

`http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/`にアクセス→tokenを入力してログイン

[kubectlの接続設定ファイル（kubeconfig）の概要](https://qiita.com/immrshc/items/91208a9b30e701d1e7f2)

