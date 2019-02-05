---
title: ビットマップからツールバー (C++) への変換
ms.date: 11/04/2016
f1_keywords:
- vc.editors.newtoolbarresource
helpviewer_keywords:
- bitmaps [C++], converting to toolbars
- Toolbar editor [C++], converting bitmaps
- toolbars [C++], converting bitmaps
- New Toolbar Resource dialog box [C++]
ms.assetid: 971c181b-40f5-44be-843d-677a7c235667
ms.openlocfilehash: 31b684ff72e970a6b09748b3925564b0b372d339
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702701"
---
# <a name="converting-bitmaps-to-toolbars-c"></a>ビットマップからツールバー (C++) への変換

C++ プロジェクトで新しいツールバーを作成するには、ビットマップを変換します。 グラフィック ビットマップからツールバーのボタンのイメージに変換します。 通常はビットマップでは、ボタンごとに 1 つのイメージの 1 つのビットマップ ボタン イメージがいくつか含まれています。 イメージのサイズにすることができます。既定では、イメージの高さ、幅 16 ピクセルです。 ボタンのイメージのサイズを指定することができます、**新規ツール バー リソース** ダイアログ ボックスを選択すると**ツール バー エディター**から、**イメージ**イメージ エディターでのメニュー。

**新規ツール バー リソース** ダイアログ ボックスでは、C++ プロジェクトのツール バー リソースに追加するボタンの高さと幅を指定できます。 既定では 16 × 15 ピクセルです。

ツールバーを作成するために使用するビットマップが 2048 の最大の幅です。 設定した場合は、**ボタンの幅**512 には、4 つのボタンのみができます。 513 幅を設定する場合は、3 つのボタンのみができます。

ダイアログ ボックスには、次のプロパティ。

|プロパティ|説明|
|---|---|
|**ボタンの幅**|ツール バー リソースをビットマップ リソースから変換して、ツールバーのボタンの幅を入力する場所を提供します。 幅と高さを指定すると、画像がトリミングされ、標準ツールバーの色 (16 色) を使用する色が調整されます。|
|**ボタンの高さ**|ツール バー リソースをビットマップ リソースから変換して、ツールバーのボタンの高さを入力する場所を提供します。 幅と高さを指定すると、画像がトリミングされ、標準ツールバーの色 (16 色) を使用する色が調整されます。|

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="to-convert-bitmaps-to-a-toolbar"></a>ビットマップからツールバーに変換するには

1. 既存のビットマップ リソースを開き、[イメージ エディター](../windows/image-editor-for-icons.md)します。 (.Rc ファイルに、ビットマップがいない場合は、.rc ファイルを右クリックし、選択**インポート**、ショートカット メニューから .rc ファイルに追加するビットマップに移動し、選択**オープン**)。

1. **イメージ**] メニューの [選択**ツール バー エディター**します。

   **新規ツール バー リソース** ダイアログ ボックスが表示されます。 幅と高さのビットマップに合わせてアイコン イメージを変更することができます。 ツールバー エディターで、ツール バー イメージが表示されます。

1. 変換を完了するには、コマンドを変更**ID**のボタンを使用して、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)します。 新しい入力**ID**か、選択、 **ID**ドロップダウン リストから。

   > [!TIP]
   > **プロパティ**ウィンドウにはタイトル バーの画鋲ボタンが含まれています。 このボタンを選択すると、有効または無効に**自動的に隠す**ウィンドウ。 有効にする個々 のプロパティ ウィンドウを再び開くことがなく、すべてのツール バー ボタン プロパティをすばやく切り替える、**自動的に隠す**オフため、**プロパティ**ウィンドウが静止したままになります。

使用して、新しいツールバーのボタンのコマンド Id を変更することも、[プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)します。 新しいツールバーの編集方法の詳細については、次を参照してください。[作成、移動、およびツール バー ボタンの編集](../windows/creating-moving-and-editing-toolbar-buttons.md)します。

## <a name="requirements"></a>必要条件

MFC または ATL

## <a name="see-also"></a>関連項目

[ツール バーの新規作成](../windows/creating-new-toolbars.md)<br/>
[ツール バー エディター](../windows/toolbar-editor.md)<br/>
[ツール バー ボタンのプロパティ](../windows/toolbar-button-properties.md)<br/>
