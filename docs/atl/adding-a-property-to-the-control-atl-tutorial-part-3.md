---
title: コントロールへのプロパティの追加 (ATL チュートリアル、パート 3)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
ms.openlocfilehash: 288dc9f5af57c02639d15a9a971419a633cfc08d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127588"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>コントロールへのプロパティの追加 (ATL チュートリアル、パート 3)

`IPolyCtl` は、コントロールのカスタムメソッドとプロパティを含むインターフェイスであり、プロパティを追加します。

### <a name="to-add-the-property-definitions-to-your-project"></a>プロパティ定義をプロジェクトに追加するには

1. **クラスビュー**で、`Polygon` の分岐を展開します。

1. [`IPolyCtl`] を右クリックします。

1. ショートカットメニューの [**追加**] をクリックし、[**プロパティの追加**] をクリックします。 **プロパティの追加**ウィザードが表示されます。

1. **プロパティ名**として「`Sides`」と入力します。

1. **プロパティの種類**のドロップダウンリストで、[`short`] を選択します。

1. [ **OK** ] をクリックして、プロパティの追加を完了します。

1. **ソリューションエクスプローラー**から、Polygon を開き、`IPolyCtl : IDispatch` インターフェイスの末尾にある次の行を置き換えます。

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    with

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. **ソリューションエクスプローラー**から polyctl.htm を開き、`m_clrFillColor`の定義の後に次の行を追加します。

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

プロパティを設定および取得するためのスケルトン関数が用意されていますが、プロパティを格納する変数を取得するには、それに応じて関数を実装する必要があります。

### <a name="to-update-the-get-and-put-methods"></a>Get メソッドと put メソッドを更新するには

1. `m_nSides`の既定値を設定します。 Polyctl.htm のコンストラクターに行を追加して、既定の図形を三角形にします。

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. `Get` メソッドと `Put` メソッドを実装します。 `get_Sides` および `put_Sides` 関数の宣言が Polyctl.htm に追加されました。 次のように、`get_Sides` のコードを追加し、Polyctl.htm に `put_Sides` します。

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

`get_Sides` メソッドは、`pVal` ポインターを介して `Sides` プロパティの現在の値を返します。 `put_Sides` メソッドでは、コードによって、ユーザーが `Sides` プロパティを受け入れ可能な値に設定していることが確認されます。 最小値は3である必要があります。また、点の配列が各辺に使用されるため、100は最大値に対して妥当な制限となります。

これで `Sides`という名前のプロパティが作成されました。 次の手順では、描画コードを使用するように変更します。

手順[2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [.](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)に戻ります。

## <a name="see-also"></a>参照

[チュートリアル](../atl/active-template-library-atl-tutorial.md)
