[タグがついた記事の削除ができない](https://github.com/elixirjp-slack-com/realworld/issues/6)

[has_many](https://hexdocs.pm/ecto/Ecto.Schema.html#has_many/3)

> :on_delete-親レコードが削除されたときに関連付けに対して実行されるアクション。:nothing（デフォルト）、:nilify_allおよびである可能性があり:delete_allます。このオプションの使用は、ほとんどのリレーショナルデータベースでは推奨されていません。代わりに、移行でを設定しreferences(:parent_id, on_delete: :delete_all)ます。移行オプションとは反対に、このオプションは整合性を保証できず、トリガーされるだけでEcto.Repo.delete/2（オンではなく Ecto.Repo.delete_all/2）、カスケードされることはありません。投稿に多くのタグが含まれるコメントが多く、投稿を削除すると、コメントのみが削除されます。データベースが参照をサポートしていない場合は、Ecto.Multiまたはを使用してカスケードを手動で実装できますEcto.Changeset.prepare_changes/2。

[Ectoのassoc関数を整理してみる](https://zenn.dev/koga1020/articles/ca0f4f26d6f0937a3ca3)


[Elixir Ecto Association](https://qiita.com/sand/items/5581497972473e308f05)

```elixir
iex(39)> Service.get_project!(6) |> Repo.preload([:account])
[debug] QUERY OK source="projects" db=2.5ms idle=1196.1ms
SELECT p0.`id`, p0.`name`, p0.`account_id`, p0.`inserted_at`, p0.`updated_at` FROM `projects` AS p0 WHERE (p0.`id` = ?) [6]
[debug] QUERY OK source="accounts" db=5.3ms queue=0.1ms idle=1199.1ms
SELECT a0.`id`, a0.`email`, a0.`name`, a0.`hashed_password`, a0.`confirmed_at`, a0.`inserted_at`, a0.`updated_at`, a0.`id` FROM `accounts` AS a0 WHERE (a0.`id` = ?) [6]
%DietWeb.Service.Project{
  __meta__: #Ecto.Schema.Metadata<:loaded, "projects">,
  account: #DietWeb.Service.Account<
    __meta__: #Ecto.Schema.Metadata<:loaded, "accounts">,
    account_daily_stats: #Ecto.Association.NotLoaded<association :account_daily_stats is not loaded>,
    confirmed_at: nil,
    email: "seiji.sasaki+test@drecom.co.jp",
    id: 6,
    inserted_at: ~N[2022-05-24 07:32:41],
    name: "test",
    projects: #Ecto.Association.NotLoaded<association :projects is not loaded>,
    service_keys: #Ecto.Association.NotLoaded<association :service_keys is not loaded>,
    updated_at: ~N[2022-05-24 07:32:41],
    ...
  >,
  account_id: 6,
  id: 6,
  inserted_at: ~N[2022-05-24 08:12:59],
  loadtests: #Ecto.Association.NotLoaded<association :loadtests is not loaded>,
  name: "test1_project2",
  scenarios: #Ecto.Association.NotLoaded<association :scenarios is not loaded>,
  updated_at: ~N[2022-05-24 08:12:59]
}

iex(40)> Service.get_project!(6)                            
[debug] QUERY OK source="projects" db=5.9ms queue=0.1ms idle=1041.4ms
SELECT p0.`id`, p0.`name`, p0.`account_id`, p0.`inserted_at`, p0.`updated_at` FROM `projects` AS p0 WHERE (p0.`id` = ?) [6]
%DietWeb.Service.Project{
  __meta__: #Ecto.Schema.Metadata<:loaded, "projects">,
  account: #Ecto.Association.NotLoaded<association :account is not loaded>,
  account_id: 6,
  id: 6,
  inserted_at: ~N[2022-05-24 08:12:59],
  loadtests: #Ecto.Association.NotLoaded<association :loadtests is not loaded>,
  name: "test1_project2",
  scenarios: #Ecto.Association.NotLoaded<association :scenarios is not loaded>,
  updated_at: ~N[2022-05-24 08:12:59]
}
```

```
iex(10)> Repo.get(Project, 6) |> Repo.preload([:account])        
[debug] QUERY OK source="projects" db=4.2ms idle=1962.8ms
SELECT p0.`id`, p0.`name`, p0.`account_id`, p0.`inserted_at`, p0.`updated_at` FROM `projects` AS p0 WHERE (p0.`id` = ?) [6]
[debug] QUERY OK source="accounts" db=4.5ms idle=1967.7ms
SELECT a0.`id`, a0.`email`, a0.`name`, a0.`hashed_password`, a0.`confirmed_at`, a0.`inserted_at`, a0.`updated_at`, a0.`id` FROM `accounts` AS a0 WHERE (a0.`id` = ?) [6]
%DietWeb.Service.Project{
  __meta__: #Ecto.Schema.Metadata<:loaded, "projects">,
  account: #DietWeb.Service.Account<
    __meta__: #Ecto.Schema.Metadata<:loaded, "accounts">,
    account_daily_stats: #Ecto.Association.NotLoaded<association :account_daily_stats is not loaded>,
    confirmed_at: nil,
    email: "seiji.sasaki+test@drecom.co.jp",
    id: 6,
    inserted_at: ~N[2022-05-24 07:32:41],
    name: "test",
    projects: #Ecto.Association.NotLoaded<association :projects is not loaded>,
    service_keys: #Ecto.Association.NotLoaded<association :service_keys is not loaded>,
    updated_at: ~N[2022-05-24 07:32:41],
    ...
  >,
  account_id: 6,
  id: 6,
  inserted_at: ~N[2022-05-24 08:12:59],
  loadtests: #Ecto.Association.NotLoaded<association :loadtests is not loaded>,
  name: "test1_project2",
  scenarios: #Ecto.Association.NotLoaded<association :scenarios is not loaded>,
  updated_at: ~N[2022-05-24 08:12:59]
}

iex(11)> Repo.get(Project, 100) |> Repo.preload([:account])
[debug] QUERY OK source="projects" db=6.5ms idle=1194.9ms
SELECT p0.`id`, p0.`name`, p0.`account_id`, p0.`inserted_at`, p0.`updated_at` FROM `projects` AS p0 WHERE (p0.`id` = ?) [100]
nil
iex(12)> Repo.get(Project, 100)                            
[debug] QUERY OK source="projects" db=4.9ms idle=1068.0ms
SELECT p0.`id`, p0.`name`, p0.`account_id`, p0.`inserted_at`, p0.`updated_at` FROM `projects` AS p0 WHERE (p0.`id` = ?) [100]
nil
```

[Elixir Ecto Association](https://qiita.com/sand/items/5581497972473e308f05)
