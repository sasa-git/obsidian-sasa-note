ASGのインスタンスタイプの変更は、変更してから即インスタンスが置き換わるのではなく、新規にインスタンス起動時にASGの設定が適用されていくイメージ

4台起動する
![/assets/mod_setting_test1.png]

起動するインスタンスタイプはt3, m5, m6i
![/assets/mod_setting_test2.png]

起動しているインスタンス状態 t3: 3台、m5: 1台
![/assets/mod_setting_test3.png]

起動するインスタンスタイプからt3を削除
![/assets/mod_setting_test4.png]

ASGの設定を変更しても、t3インスタンスは勝手に落とされない
![/assets/mod_setting_test5.png]

t3のインスタンスを落とす
![/assets/mod_setting_test6.png]

新しくm5インスタンスが起動
![/assets/mod_setting_test7.png]

他のt3インスタンスを落としたら、ちゃんとt3以外が起動しているのを確認
![/assets/mod_setting_test8.png]
