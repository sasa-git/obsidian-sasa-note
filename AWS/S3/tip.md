### S3 Glacierの料金
> S3 Glacier Flexible Retrieval と S3 Glacier Deep Archive ストレージクラスでは、適切なストレージクラス料金が課される S3 Glacier のインデックスとメタデータに対して、オブジェクトあたり 32 KB のデータがさらに必要となります。Amazon S3 では、S3 Glacier Flexible Retrieval と S3 Glacier Deep Archive にアーカイブされるオブジェクトのユーザー定義名とメタデータを保存して維持するために、オブジェクトごとに 8 KB が必要です。
> S3 Glacier Instant Retrieval の課金対象となる最小オブジェクトサイズは 128 KB です。128 KB より小さいサイズのオブジェクトを保存することもできますが、適切なストレージクラス料金で 128 KB のストレージとして課金されます。
> S3 Glacier Flexible Retrieval または S3 Glacier Deep Archive に保存されている各オブジェクトの場合、Amazon S3 はメタデータに対する課金可能な 40 KB のオーバーヘッドを追加し、それは、S3 標準レートで請求される 8 KB と S3 Glacier Flexible Retrieval または S3 Deep Archive レートで請求される 32 KB から構成されます。

[【AWS】S3ストレージクラスを適切に使い分ける](https://sayjoyblog.com/s3_storage_classes/)

[S3からGlacierにライフサイクルで移行するときにお金がかかるので注意](https://blog.jicoman.info/2018/07/noticement-of-transition-from-s3-glacier/)

[CloudTrailの証跡データをS3ライフサイクルでGlacierに移行する際の損益分岐点を探る](https://dev.classmethod.jp/articles/explore-breakeven-points-when-migrating-cloudtrail-trail-data-to-glacier-in-s3-lifecycles/#toc-3)

[ライフサイクルポリシーでGlacierに移行するのは実は損？？](https://qiita.com/Ichi0124/items/19a05ea599bd13372586)

