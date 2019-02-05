---
title: 複数のメニューやメニュー コマンド (C++) の編集
ms.date: 11/04/2016
helpviewer_keywords:
- menu commands [C++], selecting
- menus [C++], selecting
- commands [C++], menu commands
- commands [C++], copying on menus
- menu items, moving
- commands [C++], moving on menus
- menu items, copying
- menu items, deleting
- commands [C++], deleting from menus
- menus [C++], deleting
ms.assetid: b6f17897-2a40-4afd-97d4-a38b7661680b
ms.openlocfilehash: 45e2c4e97dc850b4d6fb13a5526911e4bd5caec2
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703221"
---
# <a name="editing-multiple-menus-or-menu-commands"></a>複数のメニューやメニュー コマンドの編集

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="to-select-multiple-menu-commands"></a>複数のメニュー コマンドを選択するには

複数のメニュー名または削除、またはプロパティを変更するなどの一括操作を実行するメニュー コマンドを選択することができます。

押しながら、 **Ctrl**キーで、メニューまたはサブメニューのコマンドを選択します。

## <a name="to-move-and-copy-menus-and-menu-commands"></a>移動し、メニューとメニュー コマンドをコピーするには

ドラッグ アンド ドロップ操作またはショートカット メニュー (右クリック メニュー) のコマンドを使用して、メニューとメニュー コマンドを移動またはコピーすることができます。

### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>ドラッグ アンド ドロップ操作を使用してメニューやメニュー コマンドを移動またはコピーするには

1. 移動する項目を次の場所にドラッグまたはコピーします。

   - 現在のメニュー上の新しい場所。

   - 別のメニュー (他のメニューに移動するには、そのメニューにマウス ポインターをドラッグします)。

1. 挿入ガイドで目的の位置が示されたら、メニュー コマンドをドロップします。

### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>ショートカット メニューのコマンドを使用してメニューやメニュー コマンドを移動またはコピーするには

1. 1 つ以上のメニューまたはメニュー コマンドを右クリックします。

1. ショートカット メニューの **[切り取り]** (移動する場合) または **[コピー]** を選択します。

1. 別のメニュー項目を移動する場合はリソースまたはリソース スクリプト ファイル、[別のウィンドウで開きます](/visualstudio/ide/customizing-window-layouts-in-visual-studio)します。

1. メニューやメニュー コマンドを移動またはコピーする位置を選択します。

1. ショートカット メニューの **[貼り付け]** を選択します。 移動またはコピーする項目は、選択した項目の前に配置されます。

   > [!NOTE]
   > ドラッグでコピーした項目を別のメニュー ウィンドウの別のメニューに貼り付けることもできます。

## <a name="to-delete-a-menu-or-menu-command"></a>メニューまたはメニュー コマンドを削除するには

1. メニュー名またはコマンドを右クリックします。

1. ショートカット メニューの **[削除]** を選択します。

   > [!NOTE]
   > 同様に、ショートカット メニューを使用して、コピー、切り取り、貼り付け、新しい項目の挿入、区切り記号の挿入、ID の編集、ポップアップとして表示、ニーモニックの確認などの操作を実行することができます。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[メニュー エディター](../windows/menu-editor.md)