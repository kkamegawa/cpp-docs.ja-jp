---
title: メニュー (C++) の作成
ms.date: 11/04/2016
f1_keywords:
- vc.editors.menu
helpviewer_keywords:
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
- menus [C++], adding items
- commands [C++], adding to menus
- menu items, adding to menus
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: 438480032f1fe9208e406b4ee499267e42148a48
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702805"
---
# <a name="creating-a-menu-c"></a>メニュー (C++) の作成

> [!NOTE]
> **リソース ウィンドウ**Express エディションでは使用できません。

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="to-create-a-standard-menu"></a>標準メニューを作成するには

1. **ビュー**メニューの **リソース ビュー**を右クリックし、**メニュー**見出しと選択**リソースの追加**します。 **[メニュー]** をクリックします。

1. メニュー バーで、"ここへ入力" と表示されている四角形の **[新しい項目]** ボックスを選びます。

   ![メニュー エディターの新しい項目ボックス](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   [新しい項目] ボックス

1. たとえば「ファイル」など、新しいメニューの名前を入力します。

   入力したテキストは、 **メニュー** エディターと、 **プロパティ ウィンドウ** の [[キャプション]](/visualstudio/ide/reference/properties-window)ボックスの両方に表示されます。 新しいメニューのプロパティはこのどちらからでも編集できます。

   メニュー バーで新しいメニューの名前を指定すると、さらに別のメニューを追加できるように [新しい項目] ボックスが右に移動し、最初のメニューの下に新しい [新しい項目] ボックスが表示されます。この新しいボックスでメニュー コマンドを追加できます。

   ![展開された 新しい項目ボックス](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   メニュー名の入力後にフォーカスが移動した [新しい項目] ボックス

   > [!NOTE]
   > メニュー バーの単一項目のメニューを作成するには、設定、**ポップアップ**プロパティを**False**します。

## <a name="to-insert-a-new-menu-between-existing-menus"></a>既存のメニュー間に新規メニューを挿入するには

既存のメニューの名前とキーを押して選択、**挿入**キー。 **新しい項目の**ボックスが選択した項目の前に挿入されます。

   \- または -

メニュー バーを右クリックし、選択**Insert New**ショートカット メニューから。

## <a name="to-add-commands-to-a-menu"></a>メニューにコマンドを追加するには

1. メニューを作成します。

1. たとえば、メニューの名前を選択**ファイル**します。

   各メニューが展開され、コマンド用の新しい項目ボックスが表示されます。 コマンドを追加するなど、**新規**、**オープン**と**閉じる**を**ファイル**メニュー。

1. [新しい項目] ボックスに新しいメニュー コマンドの名前を入力します。

   > [!NOTE]
   > 入力したテキストは、 **メニュー** エディターと、 **プロパティ ウィンドウ** の [[キャプション]](/visualstudio/ide/reference/properties-window)ボックスの両方に表示されます。 新しいメニューのプロパティはこのどちらからでも編集できます。

   > [!TIP]
   > ユーザーがメニュー コマンドを選択できるようにするニーモニック キー (ホット キー) を定義することができます。 アンパサンドを入力 (`&`) ニーモニックとして指定する文字の前にします。 この文字を入力することで、ユーザーはメニュー コマンドを選択できます。

1. **プロパティ**ウィンドウで、メニュー コマンドを適用するプロパティを選択します。 詳細については、次を参照してください。[メニュー コマンドのプロパティ](../windows/menu-command-properties.md)します。

1. **プロンプト**ボックスに、**プロパティ**ウィンドウで、アプリケーションのステータス バーに表示するプロンプト文字列を入力します。

   この手順では、作成したメニュー コマンドと同じリソース識別子を持つ文字列テーブルにエントリを作成します。

   > [!NOTE]
   > プロンプトがメニュー項目に適用できるだけ、**ポップアップ**プロパティの**True**します。 たとえば、トップレベルのメニュー項目にサブメニュー項目がある場合、プロンプトを適用できます。 目的を**プロンプト**をどうなるかを示すためには、ユーザーがメニュー項目を選択した場合。

1. キーを押して**Enter**メニュー コマンドを完了します。

   新しい項目ボックスが選択され、追加のメニュー コマンドを作成できるようになります。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[メニュー エディター](../windows/menu-editor.md)