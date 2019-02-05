---
title: メニュー コマンド (C++) の関連付け
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [C++], menu association
- commands [C++], associating menu commands with accelerator keys
- menu commands [C++], associating with keyboard shortcuts
- status bars [C++], associating menu items
- menus [C++], status bar text
- access keys [C++], checking
- menus [C++], shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics [C++], adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics [C++], uniqueness checking
- Check Mnemonics command
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
ms.openlocfilehash: f72fe5de3ef29b9575ef1a3138d4d114d7470fee
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703039"
---
# <a name="associating-menu-commands-c"></a>メニュー コマンド (C++) の関連付け

メニュー コマンドとキーボードの組み合わせで同じプログラム コマンドを発行したいと思うことはよくあります。 使用して同じコマンドを発行、**メニュー**エディター メニュー コマンドをアプリケーションのアクセラレータ テーブル内のエントリに同じリソース識別子を割り当てできます。 次に、メニュー コマンドの [キャプション](../windows/menu-command-properties.md) を編集して、アクセラレータ キーの名前を表示します。

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

## <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>メニュー コマンドをアクセラレータ キーと関連付けるには

1. **メニュー** エディターで、目的のメニュー コマンドを選択します。

1. [プロパティ ウィンドウ](/visualstudio/ide/reference/properties-window)で、アクセラレータ キーの名前を **キャプション** プロパティに追加します。

   - メニューのキャプションに続いて、タブ (\t) のエスケープ シーケンスを入力し、すべてのメニューのアクセラレータ キーが左揃えされるようにします。

   - 修飾子キーの名前を入力 (**Ctrl**、 **Alt**、または**Shift**) プラス記号 (**+**) と名前、文字、または追加のキーの記号です。

       割り当てるにはたとえば、 **Ctrl**+**O**を**オープン**コマンドを**ファイル**] メニューの [メニュー コマンドを変更します。**キャプション**次のテキストのように見えるようにします。

        ```
        &Open...\tCtrl+O
        ```

       メニュー コマンド、**メニュー**エディターは、入力すると、新しいキャプションを反映するように更新されます。

1. [アクセラレータ](../windows/adding-an-entry-to-an-accelerator-table.md) エディターで **アクセラレータ テーブル エントリ** を作成し、メニュー コマンドと同じ識別子をそれに割り当てます。 使用するキーの組み合わせは、覚えやすいものにしてください。

## <a name="to-associate-a-menu-command-with-a-status-bar-text-string-in-mfc-applications"></a>ステータス バーのテキスト文字列の MFC アプリケーションでメニュー コマンドを関連付けるには

MFC アプリケーションでは、各ユーザーが選択メニュー コマンドの説明のテキストを表示できます。 各メニュー コマンドを使用するテキスト文字列を割り当てることでわかりやすいテキストを表示、**プロンプト**プロパティ、**プロパティ**ウィンドウ。 コマンドと同じ ID を持つ [ストリング テーブル](../windows/string-editor.md) に文字列がある場合、MFC アプリケーションでは、ユーザーがマウス ポインターをメニュー項目の上に置くと、実行中のアプリケーションのステータス バーにこの文字列リソースが自動的に表示されます。

1. **メニュー** エディターで、メニュー コマンドを選択します。

1. [[プロパティ] ウィンドウ](/visualstudio/ide/reference/properties-window)で、関連付けるステータス バーのテキストを **[プロンプト]** ボックスに入力します。

> [!NOTE]
> この一連の手順では、MFC が必要です。

## <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>メニュー コマンドにアクセス (ショートカット) キーを割り当てるには

C++ プロジェクトで、メニューとメニュー コマンドにアクセス キー (ユーザーがキーボードを使用してメニューを選択できるようにするニーモニック) を割り当てることができます。

アンパサンドを入力 (`&`) メニュー名やコマンド名、対応するアクセス キーとしてその文字を指定する文字の前にします。 たとえば、"& File"のセット**Alt**+**F**のショートカット キーとして、**ファイル**Microsoft Windows 用に記述されたアプリケーションでメニュー。

   メニュー項目は、文字の 1 つがショートカット キーに割り当てられている表示可能キューを提供します。 アンパーサンドに続く文字は、下線付きで表示されます (オペレーティング システムによって異なる)。

   > [!NOTE]
   > メニューを右クリックし、ショートカット メニューから **[ニーモニックの確認]** を選択して、メニューのすべてのアクセスキーが一意であることを確認してください。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[メニュー エディター](../windows/menu-editor.md)<br/>
[メニューへのコマンドの追加](../windows/adding-commands-to-a-menu.md)<br/>
[文字列 (ATL と MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
