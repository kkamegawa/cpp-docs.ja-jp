---
title: プロパティ ページの実装 (ATL)
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
ms.openlocfilehash: 68b4aaef06e40a8ec7b00f9ba744d83ce3388da2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492378"
---
# <a name="example-implementing-a-property-page"></a>例:プロパティ ページの実装

::: moniker range="vs-2019"

ATL プロパティ ページ ウィザードは、Visual Studio 2019 以降では使用できません。

::: moniker-end

::: moniker range="<=vs-2017"

この例では、[ドキュメント クラス](../mfc/document-classes.md) インターフェイスのプロパティを表示する (変更することもできる)プロパティ ページの作成方法を示します。

この例は、[ATLPages の例](../overview/visual-cpp-samples.md)をベースにしています。

この例を完了するには、以下を行います。

- [クラスの追加] ダイアログ ボックスと ATL プロパティ ページ ウィザードを使用して、[Add the ATL プロパティ ページ クラスを追加します](#vcconusing_the_atl_object_wizard)。

- `Document` インターフェイスの関心のあるプロパティ用の新しいコントロールを追加することで、[ダイアログ リソースを編集します](#vcconediting_the_dialog_resource)。

- ユーザーが行った変更のプロパティ ページ サイトへの通知を維持するために、[メッセージ ハンドラーを追加します](#vcconadding_message_handlers)。

- いくつかの `#import` ステートメントと typedef を [ハウスキープ処理](#vcconhousekeeping)セクションに追加します。

- プロパティ ページに渡されるオブジェクトを検証するために [IPropertyPageImpl::SetObjects をオーバーライドします](#vcconoverriding_ipropertypageimpl_setobjects)。

- プロパティ ページのインターフェイスを初期化するために [IPropertyPageImpl::Activate をオーバーライドします](#vcconoverriding_ipropertypageimpl_activate)。

- オブジェクトを最新のプロパティ値で更新するために [ IPropertyPageImpl::Apply をオーバーライドします](#vcconoverride_ipropertypageimpl_apply)。

- シンプルなヘルパー オブジェクトを作成することで、[プロパティ ページを表示します](#vccontesting_the_property_page)。

- プロパティ ページをテストする[マクロを作成します](#vcconcreating_a_macro)。

##  <a name="vcconusing_the_atl_object_wizard"></a> ATL プロパティ ページ クラスの追加

まず、`ATLPages7` という名前の DLL サーバー用の新しい ATL プロジェクトを作成します。 次に、[ATL プロパティ ページ ウィザード](../atl/reference/atl-property-page-wizard.md)を使用してプロパティ ページを生成します。 プロパティ ページに **DocProperties** という**短い名前**を付けた後、 **[文字列]** ページに切り替えて、次の表に示すプロパティ ページに固有の項目を設定します。

|アイテム|値|
|----------|-----------|
|Title|TextDocument|
|Doc String|VCUE TextDocument のプロパティ|
|Helpfile|*\<空白>*|

このウィザード ページに設定した値は、プロパティ ページ コンテナーが `IPropertyPage::GetPageInfo` を呼び出したときに返されます。 その後の文字列の処理はコンテナーによって決まりますが、通常は、ユーザーがページを識別するために使用されます。 Title は、通常、ページ上部のタブに表示され、Doc String は、ステータス バーまたはツールヒント上に表示できます (ただし、標準プロパティ フレームではこの文字列はまったく使用されません)。

> [!NOTE]
>  ここで設定した文字列は、ウィザードによって、文字列リソースとしてプロジェクトに格納されます。 ページのコードが生成された後でこれらの文字列の情報を変更する必要がある場合は、リソース エディターを使用して簡単に編集できます。

**[OK]** をクリックして、ウィザードでプロパティ ページを生成します。

##  <a name="vcconediting_the_dialog_resource"></a> ダイアログ リソースの編集

これでプロパティ ページが生成されたので、ページを表すダイアログ リソースにいくつかのコントロールを追加する必要があります。 次に示すように、編集ボックス、静的テキスト コントロール、およびチェック ボックスを追加し、それらの ID を設定します。

![ダイアログ リソースの編集](../atl/media/ppgresourcelabeled.gif "ダイアログ リソースの編集")

これらのコントロールは、ドキュメントのファイル名とその読み取り専用状態を表示するために使用されます。

> [!NOTE]
>  期待に反して、ダイアログ リソースには、フレームもコマンド ボタンも含まれず、タブも表示されません。 これらの機能は、たとえば [OleCreatePropertyFrame](/windows/win32/api/olectl/nf-olectl-olecreatepropertyframe) を呼び出すことで作成されるプロパティ ページ フレームによって提供されます。

##  <a name="vcconadding_message_handlers"></a> メッセージ ハンドラーの追加

コントロールを用意したら、いずれかのコントロールの値が変更されたダーティ状態のページを更新するためのメッセージ ハンドラーを追加できます。

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

このコードは、[IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) を呼び出すことで、編集コントロールまたはチェック ボックスに対して行われた変更に応答し、ページが変更されたことをページ サイトに通知します。 通常、ページ サイトは、プロパティ ページ フレームの **[適用]** ボタンを有効または無効にすることで応答します。

> [!NOTE]
>  プロパティ ページでは、どのプロパティがユーザーによって変更されたかを正確に追跡して、変更されていないプロパティの更新を回避できるようにする必要があります。 この例では、元のプロパティの値を追跡し、変更を適用するときに、それらを UI の現在の値と比較することで、そのコードを実装しています。

##  <a name="vcconhousekeeping"></a> ハウスキープ処理

次に、2 つの `#import` ステートメントを DocProperties.h に追加して、コンパイラが `Document` インターフェイスを認識できるようにします。

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

さらに、`IPropertyPageImpl` 基底クラスを参照する必要があります。次の **typedef** を `CDocProperties` クラスに追加します。

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

##  <a name="vcconoverriding_ipropertypageimpl_setobjects"></a> IPropertyPageImpl::SetObjects のオーバーライド

オーバーライドする必要がある最初の `IPropertyPageImpl` メソッドは [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects) です。 ここでは、単一のオブジェクトのみが渡されていること、および想定している `Document` インターフェイスがサポートされていることをチェックするコードを追加します。

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
>  このページでは、オブジェクトのファイル名の設定をユーザーに許可するため、単一のオブジェクトのみをサポートするのが合理的であり、任意の 1 つの場所には 1 つのファイルのみが存在できます。

##  <a name="vcconoverriding_ipropertypageimpl_activate"></a> IPropertyPageImpl::Activate のオーバーライド

次の手順は、ページの初回の作成時に、基になるオブジェクトのプロパティ値を使用してプロパティ ページを初期化することです。

ここでは、プロパティの初期値は、ページのユーザーが変更を適用したときに比較対象としても使用するため、次のメンバーをクラスに追加する必要があります。

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

[Activate](../atl/reference/ipropertypageimpl-class.md#activate) メソッドの基底クラスの実装がダイアログ ボックスとそのコントロールの作成を担当するため、このメソッドをオーバーライドし、基底クラスを呼び出した後で独自の初期化処理を追加できます。

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

このコードでは、`Document` インターフェイスの COM メソッドを使用して、関心があるプロパティを取得します。 その後、[CDialogImpl](../atl/reference/cdialogimpl-class.md) によって提供される Win32 API ラッパーとその基底クラスを使用して、プロパティの値をユーザーに表示します。

##  <a name="vcconoverride_ipropertypageimpl_apply"></a> IPropertyPageImpl::Apply のオーバーライド

ユーザーがオブジェクトに変更を適用すると、プロパティ ページ サイトによって [Apply](../atl/reference/ipropertypageimpl-class.md#apply) メソッドが呼び出されます。 ここでは、`Activate` のコードとは逆の操作が行われます。`Activate` では、オブジェクトの値が取得されてプロパティ ページ上のコントロールにプッシュされますが、`Apply` では、プロパティ ページ上のコントロールから値が取得されてオブジェクトにプッシュされます。

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
>  この実装の先頭にある[m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) に対するチェックは、`Apply` が 2 回以上呼び出されたときに、オブジェクトの不必要な更新を回避するための初期チェックと同一です。 変更のみが `Document` へのメソッド呼び出しになるように、各プロパティ値に対するチェックも存在します。

> [!NOTE]
> `Document` は `FullName` を読み取り専用プロパティとして公開します。 プロパティ ページに加えられた変更に基づいて、ドキュメントのファイル名を更新するには、`Save` メソッドを使用して、別の名前でファイルを保存する必要があります。 このため、プロパティ ページのコード自体をプロパティの取得または設定に制限する必要はありません。

##  <a name="vccontesting_the_property_page"></a> プロパティ ページの表示

このページを表示するには、単純なヘルパー オブジェクトを作成する必要があります。 ヘルパー オブジェクトは、単一のオブジェクトに接続された単一のページを表示するための `OleCreatePropertyFrame` API を簡素化するメソッドを提供します。 このヘルパーは、Visual Basic から使用できるように設計されます。

[[クラスの追加] ダイアログ ボックス](../ide/add-class-dialog-box.md)と [ATL シンプル オブジェクト ウィザード](../atl/reference/atl-simple-object-wizard.md)を使用して新しいクラスを作成し、その短い名前として `Helper` を使用します。 作成したら、次の表に示すように、メソッドを追加します。

|アイテム|値|
|----------|-----------|
|メソッド名|`ShowPage`|
|パラメーター|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

*bstrCaption* パラメーターは、ダイアログ ボックスのタイトルとして表示されるキャプションです。 *bstrID* パラメーターは、CLSID または表示するプロパティ ページの ProgID を表す文字列です。 *pUnk* パラメーターは、プロパティがプロパティ ページによって構成されるオブジェクトの `IUnknown` ポインターになります。

次に示すように、メソッドを実装します。

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

##  <a name="vcconcreating_a_macro"></a> マクロの作成

プロジェクトを作成したら、Visual Studio 開発環境で作成して実行できる単純なマクロを使用して、プロパティ ページとヘルパー オブジェクトをテストできます。 このマクロは、ヘルパー オブジェクトを作成した後、**DocProperties** プロパティ ページの ProgID と Visual Studio エディターで現在アクティブになっているドキュメントの `IUnknown` ポインターを使用して、`ShowPage` メソッドを呼び出します。 このマクロで必要なコードを次に示します。

```vb
Imports EnvDTE
Imports System.Diagnostics

Public Module AtlPages

Public Sub Test()
    Dim Helper
    Helper = CreateObject("ATLPages7.Helper.1")

    On Error Resume Next
    Helper.ShowPage( ActiveDocument.Name, "ATLPages7Lib.DocumentProperties.1", DTE.ActiveDocument )
End Sub

End Module
```

このマクロを実行すると、ファイル名と現在アクティブなテキスト ドキュメントの読み取り専用状態を示すプロパティ ページが表示されます。 ドキュメントの読み取り専用状態は、開発環境でドキュメントに書き込むことができることを反映しているだけです。それは、ディスク上のファイルの読み取り専用属性には影響しません。

::: moniker-end

## <a name="see-also"></a>関連項目

[プロパティ ページ](../atl/atl-com-property-pages.md)<br/>
[ATLPages の例](../overview/visual-cpp-samples.md)
