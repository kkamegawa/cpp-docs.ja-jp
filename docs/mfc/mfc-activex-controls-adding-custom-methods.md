---
title: MFC ActiveX コントロール:カスタム メソッドの追加
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
- PtInCircle custom method [MFC]
ms.assetid: 8f8dc344-44a0-4021-8db5-4cdd3d700e18
ms.openlocfilehash: 4f5a7dc844d80ae94df8af7c0b2eea141376f9e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160147"
---
# <a name="mfc-activex-controls-adding-custom-methods"></a>MFC ActiveX コントロール:カスタム メソッドの追加

実装されていないことで、ストック メソッドのカスタム メソッドとは異なる`COleControl`します。 コントロールに追加する各カスタム メソッドの実装を指定する必要があります。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

ActiveX コントロールのユーザーは、コントロールに固有の操作を実行するには、いつでもカスタム メソッドを呼び出すことができます。 カスタム メソッドのディスパッチ マップ エントリは、フォーム DISP_FUNCTION のです。

##  <a name="_core_adding_a_custom_method_with_classwizard"></a> カスタム メソッドの追加、メソッド追加ウィザード

次の手順では、ActiveX コントロールのスケルトン コードに PtInCircle カスタム メソッドを追加することを示します。 PtInCircle は、コントロールに渡される座標が内側または外側の円かどうかを判断します。 これと同じ手順が他のカスタム メソッドを追加することもできます。 自分のカスタム メソッドの名前と PtInCircle メソッドの名前およびパラメーターについては、そのパラメーターに置き換えてください。

> [!NOTE]
>  この例では、`InCircle`記事イベントからの関数。 この関数の詳細については、記事を参照してください。 [MFC ActiveX コントロール。ActiveX コントロールにカスタム イベントの追加](../mfc/mfc-activex-controls-adding-custom-events.md)します。

#### <a name="to-add-the-ptincircle-custom-method-using-the-add-method-wizard"></a>メソッドの追加ウィザードを使用して、PtInCircle カスタム メソッドを追加するには

1. コントロールのプロジェクトを読み込みます。

1. [クラス ビュー] で、コントロールのライブラリ ノードを展開します。

1. コントロールのインターフェイス ノード (ライブラリ ノードの 2 番目のノード) を右クリックし、ショートカット メニューを開きます。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**メソッドの追加**します。

   メソッドの追加ウィザードが開きます。

1. **メソッド名**ボックスに「 *PtInCircle*します。

1. **内部名**ボックスで、メソッドの内部関数の名前を入力するか、既定値を使用して (この場合、 *PtInCircle*)。

1. **戻り値の型**ボックスで、 **VARIANT_BOOL**メソッドの戻り値の型。

1. 使用して、**パラメーターの型**と**パラメーター名**という名前のパラメーターを追加するコントロール、 *xCoord* (型*OLE_XPOS_PIXELS*)。

9. 使用して、**パラメーターの型**と**パラメーター名**という名前のパラメーターを追加するコントロール、 *yCoord* (型*OLE_YPOS_PIXELS*)。

10. **[完了]** をクリックします。

##  <a name="_core_classwizard_changes_for_custom_methods"></a> カスタム メソッドのメソッド ウィザードの変更を追加します。

カスタム メソッドを追加すると、いくつかの変更はコントロール クラスのヘッダーに、メソッドの追加ウィザード (します。H) と実装 (します。CPP) ファイル。 次の行は、コントロール クラスのヘッダーで、宣言のディスパッチ マップに追加されます (します。H) ファイル:

[!code-cpp[NVC_MFC_AxUI#18](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_1.h)]

このコードと呼ばれるディスパッチ メソッドのハンドラーを宣言して`PtInCircle`します。 外部名を使用してコントロールのユーザーによってこの関数を呼び出すことが`PtInCircle`します。

コントロールの次の行が追加されます。IDL ファイル:

[!code-cpp[NVC_MFC_AxUI#19](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_2.idl)]

この行を割り当てます、`PtInCircle`メソッド固有の ID 番号、メソッド追加ウィザードのメソッドとプロパティの一覧で、メソッドの位置。 メソッドの追加ウィザードを使用して、カスタム メソッドを追加、ので、プロジェクトに、エントリが自動的に追加されました。IDL ファイルです。

さらに、次の行はクラスの実装 (します。コントロール クラスの CPP) ファイルは、コントロールのディスパッチ マップに追加されます。

[!code-cpp[NVC_MFC_AxUI#20](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_3.cpp)]

DISP_FUNCTION マクロは、メソッドをマップ`PtInCircle`コントロールのハンドラー関数に`PtInCircle`、するのには、戻り値の型を宣言します**VARIANT_BOOL**、型の 2 つのパラメーターを宣言および**VTS_XPOS_PIXELS**と**VTS_YPOSPIXELS**に渡される`PtInCircle`します。

最後に、メソッドの追加ウィザードは、スタブ関数を追加します。`CSampleCtrl::PtInCircle`コントロールの実装の下に (します。CPP) ファイルです。 `PtInCircle`既に説明したように機能するために変更する必要が次のようにします。

[!code-cpp[NVC_MFC_AxUI#21](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-methods_4.cpp)]

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[[クラス ビュー] ウィンドウとオブジェクト ブラウザーのアイコン](/visualstudio/ide/class-view-and-object-browser-icons)
