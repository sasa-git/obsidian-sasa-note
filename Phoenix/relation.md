[タグがついた記事の削除ができない](https://github.com/elixirjp-slack-com/realworld/issues/6)

[has_many](https://hexdocs.pm/ecto/Ecto.Schema.html#has_many/3)

> :on_delete-親レコードが削除されたときに関連付けに対して実行されるアクション。:nothing（デフォルト）、:nilify_allおよびである可能性があり:delete_allます。このオプションの使用は、ほとんどのリレーショナルデータベースでは推奨されていません。代わりに、移行でを設定しreferences(:parent_id, on_delete: :delete_all)ます。移行オプションとは反対に、このオプションは整合性を保証できず、トリガーされるだけでEcto.Repo.delete/2（オンではなく Ecto.Repo.delete_all/2）、カスケードされることはありません。投稿に多くのタグが含まれるコメントが多く、投稿を削除すると、コメントのみが削除されます。データベースが参照をサポートしていない場合は、Ecto.Multiまたはを使用してカスケードを手動で実装できますEcto.Changeset.prepare_changes/2。

