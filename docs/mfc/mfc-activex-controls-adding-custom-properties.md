---
title: MFC ActiveX コントロール:カスタム プロパティの追加
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], properties
- properties [MFC], custom
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
ms.openlocfilehash: e02d5523b894f89aa93c8d2765a128920afa2353
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392779"
---
# <a name="mfc-activex-controls-adding-custom-properties"></a>MFC ActiveX コントロール:カスタム プロパティの追加

カスタム プロパティが既に実装されていないことに、ストック プロパティのカスタム プロパティとは異なる、`COleControl`クラス。 カスタム プロパティを使用して、特定の状態やコントロールを使用するプログラマに ActiveX コントロールの外観を公開できます。

この記事では、プロパティの追加ウィザードを使用して ActiveX コントロールにカスタム プロパティを追加する方法について説明し、結果として得られるコードの変更について説明します。 ここでは、次の内容について説明します。

- [プロパティの追加ウィザードを使用して、カスタム プロパティを追加するには](#_core_using_classwizard_to_add_a_custom_property)

- [カスタム プロパティのプロパティ ウィザードによる変更を追加します。](#_core_classwizard_changes_for_custom_properties)

カスタム プロパティは実装の 4 種類があります。メンバー変数、通知、Get と Set メソッドでは、メンバー変数とパラメーター化されました。

- メンバー変数の実装

   この実装では、コントロール クラスのメンバー変数として、プロパティの状態を表します。 プロパティの値が変更されたときに知っておく必要ない場合は、メンバー変数の実装を使用します。 次の 3 つの型のこの実装は、プロパティのサポート コード量が少なくを作成します。 メンバー変数の実装のディスパッチ マップ エントリ マクロは[DISP_PROPERTY](../mfc/reference/dispatch-maps.md#disp_property)します。

- 通知の実装を持つメンバー変数

   この実装は、メンバー変数とプロパティの追加ウィザードによって作成された関数の通知で構成されます。 通知関数は、プロパティ値の変更後に自動的にフレームワークによって呼び出されます。 変数を使用してメンバー通知の実装でプロパティ値が変更されると通知する必要があるとします。 この実装では、関数呼び出しを必要とするために多くの時間が必要です。 この実装のディスパッチ マップ エントリ マクロは[DISP_PROPERTY_NOTIFY](../mfc/reference/dispatch-maps.md#disp_property_notify)します。

- メソッドの実装を取得または設定

   この実装は、コントロール クラスのメンバー関数のペアで構成されます。 Get/set メソッドの実装に自動的にメンバーを呼び出します Get コントロールのユーザーは、プロパティの現在の値を要求したときに、関数とセット メンバー関数は、コントロールのユーザーは、プロパティの変更を要求したときにします。 必要があります、実行時のプロパティの値を計算する実際のプロパティを変更する前に、コントロールのユーザーによって渡される値を検証または読み取りまたは書き込みのみのプロパティの型を実装する場合は、この実装を使用します。 この実装のディスパッチ マップ エントリ マクロは[DISP_PROPERTY_EX](../mfc/reference/dispatch-maps.md#disp_property_ex)します。 次のセクションでは、[カスタム プロパティを追加するプロパティの追加ウィザードを使用して](#_core_using_classwizard_to_add_a_custom_property)、CircleOffset カスタム プロパティを使用して、この実装を示します。

- パラメーター化の実装

   パラメーター化された実装は、プロパティの追加ウィザードでサポートされています。 パラメーター化されたプロパティ (プロパティの配列とも呼ばれます) は、コントロールの 1 つのプロパティを一連の値へのアクセスに使用できます。 この実装のディスパッチ マップ エントリ マクロは、DISP_PROPERTY_PARAM です。 この型の実装の詳細については、次を参照してください。[パラメーター化されたプロパティを実装する](../mfc/mfc-activex-controls-advanced-topics.md)ActiveX コントロールの記事。高度なトピックです。

##  <a name="_core_using_classwizard_to_add_a_custom_property"></a> 使用して、プロパティの追加ウィザードのカスタム プロパティを追加するには

次の手順では、CircleOffset で、取得/設定メソッドの実装を使用して、カスタム プロパティを追加することを示します。 CircleOffset のカスタム プロパティは、コントロールのユーザー コントロールの外接する四角形の中心から円をオフセットを使用します。 カスタム プロパティと Get/set メソッド以外の実装を追加する手順は、よく似ています。

これと同じ手順をするその他のカスタム プロパティを追加することもできます。 CircleOffset プロパティ名およびパラメーターについて、カスタム プロパティの名前に置き換えてください。

#### <a name="to-add-the-circleoffset-custom-property-using-the-add-property-wizard"></a>プロパティの追加ウィザードを使用して CircleOffset のカスタム プロパティを追加するには

1. コントロールのプロジェクトを読み込みます。

1. [クラス ビュー] で、コントロールのライブラリ ノードを展開します。

1. コントロールのインターフェイス ノード (ライブラリ ノードの 2 番目のノード) を右クリックし、ショートカット メニューを開きます。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**プロパティの追加**します。

   開き、[プロパティの追加ウィザード](../ide/names-add-property-wizard.md)します。

1. **プロパティ名**ボックスに「 *CircleOffset*します。

1. **[実装型]** として、 **[Get/Set メソッド]** をクリックします。

1. **プロパティ型**ボックスで、**short**します。

1. Get と Set 関数の一意の名前を入力するか、既定の名前をそのまま使用します。

9. **[完了]** をクリックします。

##  <a name="_core_classwizard_changes_for_custom_properties"></a> カスタム プロパティのプロパティ ウィザードによる変更を追加します。

プロパティの追加ウィザードによって、ヘッダーに、変更 CircleOffset のカスタム プロパティを追加すると (します。H) と実装 (します。コントロール クラスの CPP) ファイル。

次の行に追加します。H ファイルと呼ばれる 2 つの関数を宣言する`GetCircleOffset`と`SetCircleOffset`:

[!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_1.h)]

コントロールには、次の行が追加されます。IDL ファイル:

[!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_2.idl)]

この行は、プロパティの追加ウィザードのメソッドとプロパティの一覧で、メソッドの位置から取得する、特定の ID 番号を CircleOffset プロパティに割り当てます。

さらに、次の行は、ディスパッチ マップに追加されます (でします。コントロール クラスの CPP ファイル)、コントロールの 2 つのハンドラー関数にマップします。

[!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_3.cpp)]

実装では、最後に、`GetCircleOffset`と`SetCircleOffset`関数は、コントロールの末尾に追加します。CPP ファイルです。 ほとんどの場合は、プロパティの値を返す Get 関数を変更します。 Set 関数には、通常、プロパティの変更の前後に実行されるコードが含まれます。

[!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-properties_4.cpp)]

注意するプロパティの追加ウィザードが自動的に追加の呼び出しに[SetModifiedFlag](../mfc/reference/colecontrol-class.md#setmodifiedflag)、セット関数の本体にします。 この関数を呼び出すと、変更をコントロールがマークされます。 コントロールが変更された場合は、コンテナーを保存するときにその新しい状態が保存されます。 コントロールの永続的な状態の一部として保存し、プロパティ値が変更されるたびに、この関数を呼び出す必要があります。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX コントロール: プロパティ](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC ActiveX コントロール: メソッド](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl クラス](../mfc/reference/colecontrol-class.md)
