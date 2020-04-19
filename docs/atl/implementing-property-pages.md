---
title: プロパティ ページの実装
ms.date: 11/04/2016
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
ms.openlocfilehash: 49058fe13457c2d0050452cbc0015575371e4043
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706896"
---
# <a name="implementing-property-pages"></a>プロパティ ページの実装

::: moniker range="vs-2019"

ATL プロパティ ページ ウィザードは、Visual Studio 2019 以降では使用できません。

::: moniker-end

::: moniker range="<=vs-2017"

プロパティ ページは、`IPropertyPage` または `IPropertyPage2` インターフェイスを実装する COM オブジェクトです。 ATL では、[[クラスの追加] ダイアログ ボックス](../ide/add-class-dialog-box.md)の [ATL プロパティ ページ ウィザード](../atl/reference/atl-property-page-wizard.md)経由のプロパティ ページの実装をサポートしています。

ATL を使用してプロパティ ページを作成するには:

- ATL ダイナミック リンク ライブラリ (DLL) サーバー プロジェクトを作成するか開きます。

- [[クラスの追加] ダイアログ ボックス](../ide/add-class-dialog-box.md)を開き、 **[ATL プロパティ ページ]** を開きます。

- プロパティ ページがアパートメント スレッドであることを確認します (ユーザー インターフェイスがあるため)。

- タイトル、説明 (ドキュメント文字列)、およびページに関連付けるヘルプ ファイルを設定します。

- 生成されたダイアログ リソースに、プロパティ ページのユーザー インターフェイスとして機能するコントロールを追加します。

- ページのユーザー インターフェイスの変更に応じて、検証の実行、ページ サイトの更新、またはページに関連付けられたオブジェクトの更新を実行します。 特に、ユーザーがプロパティ ページを変更した場合は、[IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) を呼び出します。

- 必要に応じて、次のガイドラインを使用して `IPropertyPageImpl` メソッドをオーバーライドします。

   |IPropertyPageImpl メソッド|オーバーライドの目的...|メモ|
   |------------------------------|----------------------------------|-----------|
   |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|ページに渡される複数のオブジェクトとそれらがサポートするインターフェイスの基本的なサニティ チェックを実行します。|基底クラスの実装を呼び出す前に、自分のコードを実行します。 設定されるオブジェクトが期待に沿っていない場合は、できるだけ早く呼び出しを失敗させる必要があります。|
   |[Activate](../atl/reference/ipropertypageimpl-class.md#activate)|ページのユーザー インターフェイスを初期化します (例: ダイアログのコントロールにオブジェクトの現在のプロパティ値を設定する、コントロールを動的に作成する、その他の初期化を実行する)。|自分のコードで更新を試行する前に基底クラスの実装を呼び出して、基底クラスでダイアログ ウィンドウとすべてのコントロールが作成できるようにします。|
   |[Apply](../atl/reference/ipropertypageimpl-class.md#apply)|プロパティの設定を検証し、オブジェクトを更新します。|呼び出しのトレース以外のことは行われないため、基底クラスの実装を呼び出す必要はありません。|
   |[Deactivate](../atl/reference/ipropertypageimpl-class.md#deactivate)|ウィンドウに関連する項目をクリーンアップします。|基底クラスの実装では、プロパティ ページを表すダイアログ ボックスが破棄されます。 ダイアログ ボックスが破棄される前にクリーンアップする必要がある場合は、基底クラスを呼び出す前に、自分のコードを追加する必要があります。|

プロパティ ページの実装の例については、「[例:プロパティ ページの実装](../atl/example-implementing-a-property-page.md)」を参照してください。

> [!NOTE]
> プロパティ ページに ActiveX コントロールをホストする場合は、ウィザードで生成されたクラスの派生を変更する必要があります。 基底クラスの一覧の **CDialogImpl\<CYourClass>** を **CAxDialogImpl\<CYourClass>** に置き換えます。

::: moniker-end

## <a name="see-also"></a>関連項目

[プロパティ ページ](../atl/atl-com-property-pages.md)<br/>
[ATLPages の例](../overview/visual-cpp-samples.md)
