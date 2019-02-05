---
title: 表示して、ActiveX コントロールの追加 ダイアログ ボックス (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
ms.openlocfilehash: 139407ec1d4e1bfad6bb06854dc24b86ce7014e8
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293612"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box-c"></a>表示して、ActiveX コントロールの追加 ダイアログ ボックス (C++)

Visual Studio では、ActiveX コントロールをダイアログ ボックスに挿入することができます。

**ActiveX コントロールの挿入** ダイアログ ボックスでは、使用中に、ダイアログ ボックスに ActiveX コントロールを挿入することができます、[ダイアログ エディター](../windows/dialog-editor.md)します。 このダイアログ ボックスには、次のプロパティが含まれています。

|プロパティ|説明|
|---|---|
|**ActiveX コントロール**|Active X コントロールの一覧が表示されます。 このダイアログ ボックスからコントロールを挿入するラッパー クラスを生成しません。 ラッパー クラスを必要がある場合を使用して、[クラス ビュー](/visualstudio/ide/viewing-the-structure-of-code)を作成する (詳細については、次を参照してください。[クラスの追加](../ide/adding-a-class-visual-cpp.md))。 このダイアログ ボックスで、Active X コントロールが表示されない場合は、ベンダーの指示に従って、コントロールをインストールしてみてください。|
|**パス**|ActiveX コントロールが掲載されているファイルを表示します。|

コントロールを配置することができます、**ツールボックス**ウィンドウを簡単にアクセスします。 詳細については、「[ツールボックス](/visualstudio/ide/reference/)」をご覧ください。

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="to-see-the-activex-controls-you-have-available"></a>使用可能な ActiveX コントロールを表示するには

1. ダイアログ エディターでダイアログ ボックスを開きます。

1. ダイアログ ボックスの本文内を右クリックします。

1. ショートカット メニューでは、次のように選択します。 **ActiveX コントロールの挿入**します。

   **ActiveX コントロールの挿入**システム上のすべての ActiveX コントロールを示すダイアログ ボックスが表示されます。 ダイアログ ボックスの下部には、ActiveX コントロール ファイルへのパスが表示されます。

## <a name="to-add-an-activex-control-to-a-dialog-box"></a>ダイアログ ボックスに ActiveX コントロールを追加するには

1. **ActiveX コントロールの挿入** ダイアログ ボックスで、ダイアログ ボックスに追加し、選択するコントロールを選択します。 **OK**します。

   コントロールがダイアログ ボックスに表示されます。このダイアログ ボックスで、他のコントロールでするのと同じように、コントロールの編集またはそのハンドラーの作成を行います。

   > [!NOTE]
   > ActiveX コントロールを [[ツールボックス] ウィンドウ](/visualstudio/ide/reference/toolbox)に追加することができます。

   > [!CAUTION]
   > システム上の ActiveX コントロールの中には、配布が法的に許可されていないものもあります。 コントロールをインストールしたソフトウェアのライセンス契約を参照するか、ソフトウェア会社に問い合わせてください。

   コントロールを配置することができます、**ツールボックス**ウィンドウを簡単にアクセスします。 詳細については、「[ツールボックス](/visualstudio/ide/reference/toolbox)」をご覧ください。

## <a name="to-edit-properties-for-an-activex-control"></a>ActiveX コントロールのプロパティを編集するには

独立系ベンダーによって提供される ActiveX コントロールは、独自のプロパティと特性が搭載可能性があります。 ActiveX コントロールのプロパティが表示されます、**プロパティ**ウィンドウ。 ActiveX コントロールの作成者によって作成されたすべてのプロパティ ページがさらに、表示される、**プロパティ ページ** ダイアログ ボックス (を表示する、**プロパティ ページ**特定の ActiveX コントロールをクリックして、 **プロパティ ページ**ボタン、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window))。

ActiveX コントロールの一部として付属するプロパティ シートによって、ActiveX コントロールのプロパティ ページには、さまざまなタブが表示されます。

> [!NOTE]
> 次の手順では、プロパティ ページを使用して ActiveX コントロールを編集するには適用されます。 参照および新しい ActiveX プロパティを編集することができますも**プロパティ**ウィンドウ。

1. 選択、 **ActiveX**コントロール。

1. **ビュー**メニューの **プロパティ ページ**プロパティを表示します。

1. プロパティ ページで、必要に応じて変更を加えます。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[ダイアログ ボックスのコントロール](../windows/controls-in-dialog-boxes.md)<br/>
[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[ActiveX コントロール コンテナー](../mfc/activex-control-containers.md)<br/>
[ActiveX コントロールの表示およびダイアログ ボックスへの ActiveX コントロールの追加](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)<br/>
[[ダイアログ エディター] タブ ([ツールボックス])](../windows/dialog-editor-tab-toolbox.md)<br/>
[リソース ファイル](../windows/resource-files-visual-studio.md)<br/>
