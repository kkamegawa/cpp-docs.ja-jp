---
title: ツールバー (アイコン用イメージ エディターを C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.texttool
helpviewer_keywords:
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
- toolbars [C++], showing
- toolbars [C++], hiding
- text, adding to an image
- Text Tool dialog box [C++]
- Text Tool Font dialog box [C++]
- fonts, changing on an image
- text, on images
ms.assetid: a0af4209-6273-4106-a7c1-0edecc9b5755
ms.openlocfilehash: dfbd721afd997f3151b1c20a7e0e1fb60e0c83e4
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560323"
---
# <a name="toolbar-c-image-editor-for-icons"></a>ツールバー (アイコン用イメージ エディターを C++)

**イメージ エディター**ツールバーには、描画、描画、テキストを入力する、消去、およびビューを操作するためのツールが含まれています。 オプション セレクターで、各ツールを使用するためのオプションを選択することができますも含まれています。 たとえば、さまざまなブラシの幅、拡大率、および線のスタイルから選択することができます。

> [!NOTE]
> 使用できるすべてのツール、**イメージ エディター**ツールバーも使用できます、**イメージ**メニュー (で、**ツール**コマンド)。

![イメージ エディターのツールバー](../mfc/media/vcimageeditortoolbar.gif "vcImageEditorToolbar")イメージ エディターのツールバー

使用する、**イメージ エディター**ツールバーと**オプション**セレクター、ツールを選択またはするオプションします。

> [!TIP]
> ツール バー ボタンの上にカーソルを置くとツール ヒントが表示されます。 これらのヒントは、各ボタンの機能を識別するのに役立ちます。

**オプション**セレクター、行、ブラシのストロークの幅を指定することができます。 上のアイコン、**オプション**セレクター ボタンが選択したツールを変更します。

![描画&#45;イメージ エディターのツールバーの図形セレクター](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcImageEditorToolbarOptionSelector")イメージ エディターのツールバーでオプション セレクター

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="use-the-text-tool-dialog-box"></a>テキスト ツール ダイアログ ボックスを使用してください。

使用して、**テキスト ツール** ダイアログ ボックスにテキスト カーソル、ビットマップ、またはアイコン リソースを追加します。

このダイアログ ボックスにアクセスするには、開く、[イメージ エディター](../windows/window-panes-image-editor-for-icons.md)します。 選択**ツール**から、**イメージ**メニューのおよび選択し、**テキスト ツール**コマンド。

### <a name="font-button"></a>[フォント] ボタン

開く、**テキスト ツール フォント** ダイアログ ボックスで、フォント、スタイル、またはカーソルのフォントのサイズを変更できます。 変更に表示されるテキストに適用されます、**テキスト**領域。

このダイアログ ボックスにアクセスするには、選択、**フォント**ボタン、**テキスト ツール** ダイアログ ボックス。 使用できるプロパティは次のとおりです。

|プロパティ|説明|
|---|---|
|**フォント**|使用可能なフォントが表示されます。|
|**フォント スタイル**|指定したフォントの使用可能なスタイルの一覧を表示します。|
|**Size**|指定したフォントの使用可能なポイントのサイズを一覧表示します。|
|**サンプル**|指定したフォントの設定でテキストの表示方法のサンプルが表示されます。|
|**スクリプト**|指定したフォント用の利用可能な言語のスクリプトを一覧表示します。 別の言語のスクリプトを選択すると、文字セットの多言語のドキュメントを作成するために使用可能な言語になります。|

#### <a name="to-change-the-font-of-text-on-an-image"></a>イメージのテキストのフォントを変更するには

次の手順では、Windows アプリケーションのアイコンにテキストを追加し、テキストのフォントを操作する方法の例を示します。

1. C++ Windows フォーム アプリケーションを作成します。 詳細については、次を参照してください。 [Windows アプリケーション プロジェクトを作成する](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5)します。 *App.ico*ファイルは、既定では、プロジェクトに追加されます。

1. **ソリューション エクスプ ローラー**、ファイルをダブルクリックして*app.ico*します。 [イメージ エディター](../windows/image-editor-for-icons.md)が開きます。

1. **イメージ**メニューの **ツール**選び**テキスト ツール**します。 **テキスト ツール** ダイアログ ボックスが表示されます。

1. **テキスト ツール**ダイアログ ボックスに「 *C++* 空のテキスト領域にします。 このテキストの左上隅にあるサイズ変更可能なボックスに表示されます*app.ico*の**イメージ エディター**します。

1. **イメージ エディター**、サイズ変更可能なボックス、テキストの読みやすさを向上させるために、app.ico の中央にドラッグします。

1. **テキスト ツール**ダイアログ ボックスで、**フォント**ボタンをクリックします。 **テキスト ツール フォント** ダイアログ ボックスが表示されます。

1. **テキスト ツール フォント**ダイアログ ボックスで、 **Times New Roman**記載されている利用可能なフォントの一覧から、**フォント**ボックスの一覧。

1. 選択**太字**でリストされている利用可能なフォント スタイルの一覧から、**フォント スタイル**ボックスの一覧。

1. 選択**10**ポイントで示されたサイズの使用可能な一覧から、**サイズ**ボックスの一覧。

1. **[OK]** ボタンを選択します。 **テキスト ツール フォント** ダイアログ ボックスが閉じ、新しいフォントの設定は、テキストに適用されます。

1. 選択、**閉じる**のボタンでは、**テキスト ツール** ダイアログ ボックス。 サイズ変更可能なテキストを囲むボックスから消え、**イメージ エディター**します。

### <a name="text-area"></a>テキスト領域

リソースの一部として表示されるテキストを表示します。 最初にこの領域は空です。

> [!NOTE]
> 場合**透明な背景**が設定された場合、テキストのみをイメージに配置されます。 場合**不透明な背景**設定は、塗りつぶす外接する四角形、[背景色](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md)テキストの背後に配置されます。 詳細については、次を参照してください。[不透明を選択すると透明な背景](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)します。

右クリック、**テキスト ツール** ダイアログ ボックスは、Windows の標準コマンドの一覧を含む既定のショートカット メニューにアクセスします。

## <a name="to-display-or-hide-the-image-editor-toolbar"></a>イメージ エディターのツールバーを非表示

描画ツールの多くはから利用できるため、[キーボード](../windows/accelerator-keys-image-editor-for-icons.md)、非表示にする便利な場合があります、**イメージ エディター**ツールバー。

**ビュー**メニューの **ツールバー**選択**イメージ エディター**します。

   > [!NOTE]
   > このツールバーから要素は使用できないとイメージ ファイル現在のプロジェクトからまたはソリューションがで開いていない、**イメージ エディター**します。 参照してください[アイコンまたはその他のイメージを作成する](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)、イメージ ファイルをプロジェクトに追加する方法について。

## <a name="requirements"></a>必要条件

なし

## <a name="see-also"></a>関連項目

[[色] ウィンドウ](../windows/colors-window-image-editor-for-icons.md)<br/>
[グラフィカル リソースの編集](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[アクセラレータ キー](../windows/accelerator-keys-image-editor-for-icons.md)<br/>