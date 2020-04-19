---
title: MFC ActiveX コントロール:ActiveX コントロールにおけるピクチャの使用
ms.date: 11/04/2016
f1_keywords:
- LPPICTUREDISP
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- MFC ActiveX controls [MFC], pictures
- OnDraw method [MFC]
- OnResetState method [MFC]
- CLSID_CPicturePropPage [MFC]
ms.assetid: 2e49735c-21b9-4442-bb3d-c82ef258eec9
ms.openlocfilehash: 86e9bd220d06e714030f7d44888b210ba35fd345
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239293"
---
# <a name="mfc-activex-controls-using-pictures-in-an-activex-control"></a>MFC ActiveX コントロール:ActiveX コントロールにおけるピクチャの使用

この記事では、ActiveX コントロールに共通する Picture 型と、その実装方法を説明します。 ここでは、次の内容について説明します。

- [カスタム Picture プロパティの概要](#_core_overview_of_custom_picture_properties)

- [ActiveX コントロールでのカスタム Picture プロパティの実装](#_core_implementing_a_custom_picture_property_in_your_activex_control)

- [コントロール プロジェクトへの追加](#_core_additions_to_your_control_project)

##  <a name="_core_overview_of_custom_picture_properties"></a> カスタム Picture プロパティの概要

Picture 型は、いくつかの ActiveX コントロールに共通な型のグループの 1 つです。 Picture 型は、メタファイル、ビットマップ、またはアイコンを処理して、ユーザーが ActiveX コントロールに表示される画像を指定できるようにします。 カスタム Picture プロパティは、画像オブジェクトと Get/Set 関数を使用して実装されます。これらの関数により、コントロール ユーザーは Picture プロパティにアクセスできます。 コントロール ユーザーは、ストック Picture プロパティ ページを使用してカスタム Picture プロパティにアクセスします。

標準の Picture 型のほかに、Font 型と Color 型も使用できます。 ActiveX コントロールで標準の Font 型の使用に関する詳細については、記事を参照してください。 [MFC ActiveX コントロール。フォントを使用して](../mfc/mfc-activex-controls-using-fonts.md)します。

ActiveX コントロール クラスには、コントロール内に Picture プロパティを実装するために使用できるコンポーネントがいくつか用意されています。 次のものがこれらのコンポーネントには含まれています。

- [CPictureHolder](../mfc/reference/cpictureholder-class.md) クラス。

   このクラスは、画像オブジェクトへのアクセスを容易にするほか、カスタム Picture プロパティで表示されるアイテム用の機能を提供します。

- Get/Set 関数を使用して実装される **LPPICTUREDISP**型のプロパティのサポート。

   クラス ビューを使うと、Picture 型をサポートするカスタム プロパティを簡単に追加できます。 クラス ビューでは ActiveX コントロールのプロパティを追加する方法の詳細については、この記事を参照してください。 [MFC ActiveX コントロール。プロパティ](../mfc/mfc-activex-controls-properties.md)します。

- コントロールの Picture プロパティを操作するプロパティ ページ。

   このプロパティ ページは、ActiveX コントロールで使用できる一連のストック プロパティ ページの 1 つです。 ActiveX コントロールのプロパティ ページの詳細については、記事を参照してください。 [MFC ActiveX コントロール。ストック プロパティ ページの使用](../mfc/mfc-activex-controls-using-stock-property-pages.md)

##  <a name="_core_implementing_a_custom_picture_property_in_your_activex_control"></a> ActiveX コントロールでのカスタム Picture プロパティの実装

このセクションで説明する手順を完了すると、ユーザーが選択した画像をコントロールで表示できるようになります。 ユーザーは、現在の画像を表示しているプロパティ ページを使用して、表示される画像を変更できます。そのページにある [参照] ボタンを使うと、ユーザーは別の画像を選べます。

カスタム Picture プロパティを実装する際の手順は、その他のプロパティを実装する場合とほぼ同様です。主な違いとして、このカスタム プロパティは Picture 型をサポートする必要があります。 Picture プロパティのアイテムは ActiveX コントロールで描画する必要があるため、完全に実装するには、プロパティに多くの追加や変更を行う必要があります。

カスタム Picture プロパティを実装するには、次の操作を行う必要があります。

- [コントロール プロジェクトへのコードの追加](#_core_additions_to_your_control_project)。

   標準の Picture プロパティ ページ ID、 `CPictureHolder`型のデータ メンバー、Get/Set 実装を持つ **LPPICTUREDISP** 型のカスタム プロパティを追加する必要があります。

- [コントロール クラスの一部の関数を変更](#_core_modifications_to_your_control_project)。

   ActiveX コントロールの描画に使用するいくつかの関数を変更します。

##  <a name="_core_additions_to_your_control_project"></a> コントロール プロジェクトへの追加

標準の Picture プロパティ ページのプロパティ ページの ID を追加するには、コントロール実装ファイル内の BEGIN_PROPPAGEIDS マクロの後に、次の行を挿入 (します。CPP):

[!code-cpp[NVC_MFC_AxPic#1](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_1.cpp)]

BEGIN_PROPPAGEIDS マクロのカウント パラメーターは、いずれかによっても増やす必要があります。 次の行に例を示します。

[!code-cpp[NVC_MFC_AxPic#2](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_2.cpp)]

コントロール クラスに `CPictureHolder` データ メンバーを追加するには、コントロール ヘッダー ファイル (.H) にあるコントロール クラス宣言の protected セクションの下に次の行を挿入します。

[!code-cpp[NVC_MFC_AxPic#3](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_3.h)]

データ メンバーの名前を付ける必要はありません*m_pic*; 任意の名前で十分です。

次に、Picture 型をサポートするカスタム プロパティを追加します。

#### <a name="to-add-a-custom-picture-property-using-the-add-property-wizard"></a>プロパティ追加ウィザードを使用してカスタム Picture プロパティを追加するには

1. コントロールのプロジェクトを読み込みます。

1. [クラス ビュー] で、コントロールのライブラリ ノードを展開します。

1. コントロールのインターフェイス ノード (ライブラリ ノードの 2 番目のノード) を右クリックし、ショートカット メニューを開きます。

1. ショートカット メニューから、 **[追加]** 、 **[プロパティの追加]** の順に選びます。

1. **[プロパティ名]** ボックスに、プロパティ名を入力します。 例として、この手順では `ControlPicture` を使用します。

1. **プロパティ型**ボックスで、 **IPictureDisp** <strong>\*</strong>のプロパティの型。

1. **[実装型]** として、 **[Get/Set メソッド]** をクリックします。

1. Get 関数と Set 関数に一意の名前を入力するか、既定の名前をそのまま使用します。 (この例では、既定の名前である `GetControlPicture` と `SetControlPicture` を使用します)。

9. **[完了]** をクリックします。

プロパティ追加ウィザードにより、コントロール ヘッダー ファイル (.H) にあるディスパッチ マップのコメントの間に次のコードが追加されます。

[!code-cpp[NVC_MFC_AxPic#4](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_4.h)]

また、コントロール実装 (.CPP) ファイルのディスパッチ マップに次のコードが挿入されました。

[!code-cpp[NVC_MFC_AxPic#5](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_5.cpp)]

さらに、プロパティ追加ウィザードにより、コントロール実装ファイルに次の 2 つのスタブ関数が追加されます。

[!code-cpp[NVC_MFC_AxPic#6](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_6.cpp)]

> [!NOTE]
>  コントロールのクラス名と関数名は、上記の例とは異なる場合があります。

###  <a name="_core_modifications_to_your_control_project"></a> コントロール プロジェクトの変更

コントロール プロジェクトに必要なコードを追加した後、ActiveX コントロールの描画に影響するいくつかの関数を変更する必要があります。 変更する必要がある関数は、 `OnResetState`関数、 `OnDraw`関数、カスタム Picture プロパティの Get/Set 関数で、これらはコントロール実装ファイル内にあります。 (この例では、コントロール クラスは、呼び出されます`CSampleCtrl`、`CPictureHolder`データ メンバーが呼び出される*m_pic*、カスタム picture プロパティの名前と`ControlPicture`)。

コントロールの `OnResetState` 関数で、 `COleControl::OnResetState`への呼び出しの後にオプションの行を次のように追加します。

[!code-cpp[NVC_MFC_AxPic#7](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_7.cpp)]

これにより、コントロールの画像は空白の画像に設定されます。

画像を正しく描画するには、コントロールの [関数で](../mfc/reference/cpictureholder-class.md#render) CPictureHolder::Render `OnDraw` を呼び出します。 関数を次の例のように変更します。

[!code-cpp[NVC_MFC_AxPic#8](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_8.cpp)]

コントロールのカスタム Picture プロパティの Get 関数に、次の行を追加します。

[!code-cpp[NVC_MFC_AxPic#9](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_9.cpp)]

コントロールのカスタム Picture プロパティの Set 関数に、次の行を追加します。

[!code-cpp[NVC_MFC_AxPic#10](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_10.cpp)]

デザイン時に追加された情報が実行時に反映されるようにするため、画像のプロパティを固定する必要があります。 `COleControl`派生クラスの `DoPropExchange` 関数に次の行を追加します。

[!code-cpp[NVC_MFC_AxPic#11](../mfc/codesnippet/cpp/mfc-activex-controls-using-pictures-in-an-activex-control_11.cpp)]

> [!NOTE]
>  クラス名と関数名は、上記の例とは異なる場合があります。

変更が完了したら、プロジェクトをリビルドして、カスタム Picture プロパティの新しい機能を組み込みます。その後、Test Container を使用して新しいプロパティをテストします。 Test Container にアクセスする方法について詳しくは、「 [テスト コンテナーでのプロパティとイベントのテスト](../mfc/testing-properties-and-events-with-test-container.md) 」をご覧ください。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX コントロール: フォントの使用](../mfc/mfc-activex-controls-using-fonts.md)<br/>
[MFC ActiveX コントロール: プロパティ ページ](../mfc/mfc-activex-controls-property-pages.md)
