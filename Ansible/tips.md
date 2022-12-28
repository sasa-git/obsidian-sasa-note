[Ansibleのshellモジュールで、falseコマンドを実行できない？](https://koh-sh.hatenablog.com/entry/2020/01/16/224410)

[【Ansible】初心者が Syntax Error while loading YAML.、did not find expectedで嵌った場合と対処法](https://hamutetublog.com/ansible-syntax-error/)

[[Ansible] yum モジュールで特定のパッケージがインストール済みであることを確認する](https://tekunabe.hatenablog.jp/entry/2020/04/11/ansible_assert_yum_installed)  
> latest かどうかを厳密にテストすることは不可能 (時間関数かつ外部要因に依存) なのと、{適用,テスト}コードが同じ yum module 利用だと module に bug があるとまずいので、僕ならあえてテストでは command module で rpm -q <httpd_rpm_name> して結果確認します。
> latest テストは不可能という方の補足です。例えば latest インストール後、参照 yum repo でより新しい版の追加があるとその後で実行するテストは失敗します。より安全をとると例えば最低バージョンを決めてより新しい版なら OK というようなテストにする必要があります。

[Ansible Dynamic Inventoryをつくろう！](https://qiita.com/t_nakayama0714/items/91c2d711a397df68dddc)

[Ansible ( 俺の中で ) 最強の Best Practices](https://qiita.com/kotarella1110/items/79af4485bd7985935d6b)

[\[Ansible\] 認証情報の変数名は ansible_user、ansible_password に統一したほうがよさそう](https://tekunabe.hatenablog.jp/entry/2019/02/24/ansible_auth_variables)

[特別な変数](https://docs.ansible.com/ansible/2.9_ja/reference_appendices/special_variables.html)

[Ansible でインベントリファイルを用意せずに対象ホストを指定する方法](https://tekunabe.hatenablog.jp/entry/2018/06/11/ansible_inventory_list)

[Ansible で facts 情報を表示する](https://maku.blog/p/zw7emu3/)

[Ansible 2.5 から facts は ansible_facts.* という名前空間配下でも参照可能](https://tekunabe.hatenablog.jp/entry/2018/05/04/ansible_facts_namespace)

[Ansible Gathering Factsを上手く使う方法](https://qiita.com/yumenomatayume/items/c4e6e8fa3c038e0f14b8)

[Ansibleのモジュール開発（Python実装編）](https://dev.classmethod.jp/articles/ansible-develop-module-python/)

[Ansibleでssh-agentが働いてない時は](https://qiita.com/saamonumai/items/7a0fc858294fd1244ea5)

[備忘録 Ansibleで変数ファイルを利用する](https://qiita.com/brighton0725/items/f5208c4f0e6e47579960)

[[ansible-playbook]task単位ではなく、play単位に環境変数を設定する](https://qiita.com/mikene_koko/items/0f8486f7a928bea2e747)

[Ansibleで実行結果の値を使って処理を変えたい〜registerの使い方〜](https://qiita.com/atsushi586/items/a591f1c6dee66773aaeb)

[Ansible マジック変数の一覧と内容](https://qiita.com/h2suzuki/items/15609e0de4a2402803e9)

[amazon.aws.ec2_instance_info module – Gather information about ec2 instances in AWS](https://docs.ansible.com/ansible/latest/collections/amazon/aws/ec2_instance_info_module.html#return-values)  
EC2のタグ情報を元にターゲットとなるインスタンスを決める

[[Ansible]インベントリプラグインを使ってEC2インスタンス情報を動的に取得する](https://zenn.dev/ohsawa0515/articles/enable-ec2-dynamic-inventory-by-ansible)

[タスクをグルーピング : block](https://zenn.dev/y_mrok/books/ansible-no-tsukaikata/viewer/chapter17)


