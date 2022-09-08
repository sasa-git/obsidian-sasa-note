ASGのインスタンスタイプの変更は、変更してから即インスタンスが置き換わるのではなく、新規にインスタンス起動時にASGの設定が適用されていくイメージ

4台起動する
![img](assets/mod_setting_test1.png)

起動するインスタンスタイプはt3, m5, m6i
![img](assets/mod_setting_test2.png)

起動しているインスタンス状態 t3: 3台、m5: 1台
![img](assets/mod_setting_test3.png)

起動するインスタンスタイプからt3を削除
![img](assets/mod_setting_test4.png)

ASGの設定を変更しても、t3インスタンスは勝手に落とされない
![img](assets/mod_setting_test5.png)

t3のインスタンスを落とす
![img](assets/mod_setting_test6.png)

新しくm5インスタンスが起動
![img](assets/mod_setting_test7.png)

他のt3インスタンスを落としたら、ちゃんとt3以外が起動しているのを確認
![img](assets/mod_setting_test8.png)
