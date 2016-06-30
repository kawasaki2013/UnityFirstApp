## 【問題１】答え合わせ

### ニフティクラウドmobile backend上での確認
![mBaaS](/readme-img/mBaaS.png)

* 保存されたデータを確認しましょう
 * 「データストア」をクリックすると、「`GameScore`」クラスにデータが登録されていることが確認できます。

![ans1-1](/readme-img/ans1-1.png)

### コードの答え合わせ

* 模範解答は以下です

```csharp
// **********【問題１】名前とスコアを保存しよう！**********
NCMBObject obj = new NCMBObject ("GameScore");
obj ["name"] = name;//オブジェクトに名前とスコアを設定
obj ["score"] = score;
/* ゴースト機能 */
//		obj ["Log"] = Player.posList;
obj.SaveAsync ((NCMBException e) => { //この処理でサーバーに書き込む
    if (e != null)
    {
        // 保存に失敗した場合の処理
        Debug.Log("保存に失敗しました。エラーコード:"+e.ErrorCode);
    }
    else
    {
        // 保存に成功した場合の処理
        Debug.Log("保存に成功しました。objectId:"+ obj.ObjectId);
    }
});
// **************************************************
```