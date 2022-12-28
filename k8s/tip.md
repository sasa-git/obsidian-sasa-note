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

`❯ k edit deployment/coredns -n kube-system` などでk8s上のリソースを変更するときは、事前に `export EDITOR=vim` でEDITOR環境変数をvimにしておくこと

deploymentの再起動の方法例  
`❯ k rollout restart deployment -n kube-system`

[kubectl editしたくない人のためのkubectl patchコマンド](https://qiita.com/loftkun/items/eeae3d79226491958323)

[KubernetesのPod内からの名前解決を検証する](https://blog.mosuke.tech/entry/2020/09/09/kuubernetes-dns-test/#kubernetes%E3%81%AEservice%E3%81%B8%E3%81%AE%E3%82%A2%E3%82%AF%E3%82%BB%E3%82%B9)

[Kubernetesでのコンポーネント間の通信をまとめる](https://qiita.com/walk8243/items/604aac748daeee9d8c05#%E3%82%B1%E3%83%BC%E3%82%B9%E3%83%9D%E3%83%83%E3%83%89%E9%96%93%E5%90%8C%E4%B8%80%E3%83%8D%E3%83%BC%E3%83%A0%E3%82%B9%E3%83%9A%E3%83%BC%E3%82%B9%E5%86%85)

[Kubernetesでのコンテナ間通信のレビュー](https://training.linuxfoundation.org/ja/blog/review-of-container-to-container-communications-in-kubernetes/)

