---
title: MFC ActiveX コントロール:ストック メソッドの追加
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: 29cb0d6f53d4e8fbbce12a83b2eecb8658c82697
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396393"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC ActiveX コントロール:ストック メソッドの追加

ストック メソッドは、クラスによって既に実装されている点で、カスタム メソッドとは異なります。 [COleControl](../mfc/reference/colecontrol-class.md)します。 たとえば、`COleControl`コントロールの更新メソッドをサポートしている定義済みのメンバー関数が含まれています。 このストック メソッドのディスパッチ マップ エントリは、DISP_STOCKFUNC_REFRESH です。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

`COleControl` 2 つのメソッドをサポートしています。DoClick および更新します。 更新は、すぐに、コントロールの外観を更新するコントロールのユーザーによって呼び出されます。コントロールのクリックを起動する DoClick が呼び出されるイベント。

|メソッド|ディスパッチ マップ エントリ|コメント|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK( )**|クリック イベントを発生させます。|
|`Refresh`|**DISP_STOCKPROP_REFRESH( )**|コントロールの外観はすぐに更新します。|

##  <a name="_core_adding_a_stock_method_using_classwizard"></a> ストック メソッドを使用して、追加、メソッド追加ウィザード

ストック メソッドを追加することは単純なを使用して、[メソッド追加ウィザード](../ide/add-method-wizard.md)します。 次の手順では、MFC ActiveX コントロール ウィザードを使用して作成されたコントロールに Refresh メソッドを追加することを示します。

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>メソッドの追加ウィザードを使用して、株価の更新メソッドを追加するには

1. コントロールのプロジェクトを読み込みます。

1. [クラス ビュー] で、コントロールのライブラリ ノードを展開します。

1. コントロールのインターフェイス ノード (ライブラリ ノードの 2 番目のノード) を右クリックし、ショートカット メニューを開きます。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**メソッドの追加**します。

   メソッドの追加ウィザードが開きます。

1. **メソッド名**ボックスで、**更新**します。

1. **[完了]** をクリックします。

##  <a name="_core_classwizard_changes_for_stock_methods"></a> ストック メソッドのメソッド ウィザードの変更を追加します。

ストックの Refresh メソッドは、コントロールの基本クラスでサポートされているため、**メソッド追加ウィザード**何らかの方法でコントロールのクラス宣言を変更することはできません。 コントロールのディスパッチ マップにされ、メソッドのエントリを追加、します。IDL ファイルです。 次の行は、その実装にあるコントロールのディスパッチ マップに追加されます (します。CPP) ファイル:

[!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

これにより、コントロールのユーザーに Refresh メソッドを使用可能なにします。

コントロールの次の行が追加されます。IDL ファイル:

[!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

この行では、Refresh メソッドに、特定の ID 番号が割り当てられます。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)
