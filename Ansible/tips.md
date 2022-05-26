[Ansibleのshellモジュールで、falseコマンドを実行できない？](https://koh-sh.hatenablog.com/entry/2020/01/16/224410)

[【Ansible】初心者が Syntax Error while loading YAML.、did not find expectedで嵌った場合と対処法](https://hamutetublog.com/ansible-syntax-error/)

[[Ansible] yum モジュールで特定のパッケージがインストール済みであることを確認する](https://tekunabe.hatenablog.jp/entry/2020/04/11/ansible_assert_yum_installed)  
> latest かどうかを厳密にテストすることは不可能 (時間関数かつ外部要因に依存) なのと、{適用,テスト}コードが同じ yum module 利用だと module に bug があるとまずいので、僕ならあえてテストでは command module で rpm -q <httpd_rpm_name> して結果確認します。
> latest テストは不可能という方の補足です。例えば latest インストール後、参照 yum repo でより新しい版の追加があるとその後で実行するテストは失敗します。より安全をとると例えば最低バージョンを決めてより新しい版なら OK というようなテストにする必要があります。