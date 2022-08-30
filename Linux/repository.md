[あらためてEPELリポジトリの使い方をまとめてみた](https://qiita.com/yamada-hakase/items/fdf9c276b9cae51b3633)

[yumで明示的に使用するレポジトリを指定する方法](https://qiita.com/miyakou1982/items/3c80b4ac8c572dc29cdc)  
> /etc/yum.repos.d/hoge.repoファイルのenableの項目を0に設定し、無効化しておくという管理方法もある
> この時に無効化したreposからソフトウェアパッケージをインストールするには
> `$ yum --enablerepo=rpmforge install package-to-install`
