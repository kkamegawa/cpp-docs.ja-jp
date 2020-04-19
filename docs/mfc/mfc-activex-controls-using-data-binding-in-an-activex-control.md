---
title: MFC ActiveX コントロール:ActiveX コントロールにおけるデータ バインディングの使用
ms.date: 11/19/2018
f1_keywords:
- bindable
- requestedit
- defaultbind
- displaybind
- dispid
helpviewer_keywords:
- MFC ActiveX controls [MFC], data binding
- data binding [MFC], MFC ActiveX controls
- data-bound controls [MFC], MFC ActiveX controls
- controls [MFC], data binding
- bound controls [MFC], MFC ActiveX
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
ms.openlocfilehash: e21a31b71e681cdffed555c10079c2598967543f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239543"
---
# <a name="mfc-activex-controls-using-data-binding-in-an-activex-control"></a>MFC ActiveX コントロール:ActiveX コントロールにおけるデータ バインディングの使用

ActiveX コントロールのより強力な用途の 1 つは、データ バインディングは、データベース内の特定のフィールドにバインドするコントロールのプロパティを使用します。 ユーザーは、このバインドのプロパティ内のデータを変更するとき、コントロールは、データベースとレコードのフィールドを更新する要求を通知します。 データベースでは、成功のコントロールまたは要求の失敗が通知します。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

この記事では、コントロール側でのタスクについて説明します。 データベースとの相互作用をデータ バインディングの実装は、コントロール コンテナーの責任です。 コンテナー内のデータベースとのやり取りを管理する方法はこのドキュメントの範囲外です。 データ バインド コントロールを準備する方法については、この記事の残りの部分で説明します。

![データの概念図&#45;にバインドされたコントロール](../mfc/media/vc374v1.gif "、データの概念図&#45;にバインドされたコントロール") <br/>
データ バインド コントロールの概念図

`COleControl`クラスには、データ バインディングを実装する簡単なプロセスを構成する 2 つのメンバー関数が用意されています。 最初の関数では、 [BoundPropertyRequestEdit](../mfc/reference/colecontrol-class.md#boundpropertyrequestedit)プロパティ値を変更するアクセス許可を要求するために使用します。 [BoundPropertyChanged](../mfc/reference/colecontrol-class.md#boundpropertychanged)プロパティの値が変更された後、2 番目の関数が呼び出されます。

ここでは、次のトピックについて説明します。

- [バインド可能なストック プロパティを作成します。](#vchowcreatingbindablestockproperty)

- [バインド可能な Get/set メソッドを作成します。](#vchowcreatingbindablegetsetmethod)

##  <a name="vchowcreatingbindablestockproperty"></a> バインド可能なストック プロパティを作成します。

必要になる可能性が高くなりますが、データ バインドのストック プロパティを作成することは、[バインド可能な get/set メソッド](#vchowcreatingbindablegetsetmethod)します。

> [!NOTE]
> ストック プロパティが、`bindable`と`requestedit`既定の属性。

#### <a name="to-add-a-bindable-stock-property-using-the-add-property-wizard"></a>プロパティの追加ウィザードを使用してバインド可能なストック プロパティを追加するには

1. 使用してプロジェクトを開始、 [MFC ActiveX コントロール ウィザード](../mfc/reference/mfc-activex-control-wizard.md)します。

1. コントロールのインターフェイス ノードを右クリックします。

   これは、ショートカット メニューを開きます。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**プロパティの追加**します。

1. エントリのいずれかを選択、**プロパティ名**ドロップダウン リスト。 たとえば、選択**テキスト**します。

   **テキスト**、ストック プロパティ、**バインド可能な**と**requestedit**属性は既にチェックします。

1. 次のチェック ボックスをオン、 **IDL 属性** タブ: **displaybind**と**defaultbind**プロジェクトのプロパティの定義に属性を追加します。IDL ファイルです。 これらの属性は、コントロールをユーザーに表示されるようにし、ストック プロパティの既定のバインド可能なプロパティを作成します。

この時点で、コントロールは、データ ソースからデータを表示できますが、ユーザーは、データ フィールドを更新できません。 場合は、コントロールのデータの更新、変更することもできます、 `OnOcmCommand` [例](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)関数を次のようになります。

[!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

コントロールを登録すると、プロジェクトをビルドすることができますようになりました。 ダイアログ ボックスでは、コントロールを挿入するときに、**データ フィールド**と**データソース**プロパティが追加されているし、データ ソースと、コントロールに表示するフィールドを選択できます。

##  <a name="vchowcreatingbindablegetsetmethod"></a> バインド可能な Get/set メソッドを作成します。

データ バインド メソッドを取得または設定するだけでなく作成することも、[バインド可能なストック プロパティ](#vchowcreatingbindablestockproperty)します。

> [!NOTE]
> この手順では、ActiveX コントロールをサブクラス化する Windows コントロールをプロジェクトがある前提としています。

#### <a name="to-add-a-bindable-getset-method-using-the-add-property-wizard"></a>プロパティの追加ウィザードを使用してバインド可能な get と set メソッドを追加するには

1. コントロールのプロジェクトを読み込みます。

1. **制御設定** ページで、コントロールをサブクラス化のウィンドウ クラスを選択します。 たとえば、たい場合がありますサブクラス エディット コントロール。

1. コントロールのプロジェクトを読み込みます。

1. コントロールのインターフェイス ノードを右クリックします。

   これは、ショートカット メニューを開きます。

1. ショートカット メニューでは、次のようにクリックします。**追加** をクリックし、**プロパティの追加**します。

1. プロパティ名を入力、**プロパティ名**ボックス。 使用`MyProp`この例です。

1. データ型を選択、**プロパティ型**ドロップダウン リスト ボックス。 使用**short**この例です。

1. **[実装型]** として、 **[Get/Set メソッド]** をクリックします。

1. IDL 属性 タブから次のチェック ボックスを選択します:**バインド可能な**、 **requestedit**、 **displaybind**、および**defaultbind**を追加するにはプロジェクトのプロパティの定義に属性。IDL ファイルです。 これらの属性は、コントロールをユーザーに表示されるようにし、ストック プロパティの既定のバインド可能なプロパティを作成します。

1. **[完了]** をクリックします。

1. 本体を変更、`SetMyProp`関数の次のコードが含まれるようにします。

   [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]

1. 渡されるパラメーター、`BoundPropertyChanged`と`BoundPropertyRequestEdit`関数は、プロパティに id() 属性に渡されるパラメーターであると、プロパティの dispid します。IDL ファイルです。

1. 変更、[例](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)関数の次のコードが含まれるようにします。

   [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]

1. 変更、`OnDraw`関数の次のコードが含まれるようにします。

   [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]

1. コントロール クラスのヘッダー ファイルのヘッダー ファイルのパブリック セクションに次の定義 (コンス トラクター) のメンバー変数を追加します。

   [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]

1. 次の行の最後の行を作成、`DoPropExchange`関数。

   [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]

1. 変更、`OnResetState`関数の次のコードが含まれるようにします。

   [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]

1. 変更、`GetMyProp`関数の次のコードが含まれるようにします。

   [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]

コントロールを登録すると、プロジェクトをビルドすることができますようになりました。 ダイアログ ボックスでは、コントロールを挿入するときに、**データ フィールド**と**データソース**プロパティが追加されているし、データ ソースと、コントロールに表示するフィールドを選択できます。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)
