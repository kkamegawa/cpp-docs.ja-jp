---
title: ユーザー定義のツール
ms.date: 11/19/2018
helpviewer_keywords:
- user-defined tools (MFC Extensions)
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
ms.openlocfilehash: 785e37c63653dde91176bedd0321fc58ac122c7e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180843"
---
# <a name="user-defined-tools"></a>ユーザー定義のツール

MFC には、ユーザー定義のツールがサポートしています。 ユーザー定義のツールは、外部のユーザーが指定したプログラムを実行する特別なコマンドです。 カスタマイズのプロセスを使用して、ユーザー定義のツールを管理することができます。 アプリケーション オブジェクトがから派生していない場合にこのプロセスを使用することはできませんただし、 [CWinAppEx クラス](../mfc/reference/cwinappex-class.md)します。 カスタマイズの詳細については、次を参照してください。 [MFC のカスタマイズ](../mfc/customization-for-mfc.md)します。

カスタマイズ ダイアログ ボックスが自動的にユーザー定義のツールのサポートを有効にした場合、**ツール**タブ。次の図は、**ツール**ページ。

![ツールは、[カスタマイズ] ダイアログ ボックスでタブ](../mfc/media/custdialogboxtoolstab.png "カスタマイズ ダイアログ ボックスで [ツール] タブ") <br/>
カスタマイズ ダイアログ ボックスの ツール タブ

## <a name="enabling-user-defined-tools-support"></a>ユーザー定義の有効化のツールのサポート

アプリケーションでユーザー定義のツールを有効にするには、呼び出す[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)します。 ただし、この呼び出しのパラメーターとして使用するアプリケーションのリソース ファイルでいくつかの定数をまず定義する必要があります。

リソース エディターで、該当するコマンド ID を使用するダミーのコマンドを作成します 次の例では使用する`ID_TOOLS_ENTRY`とコマンド id。 このコマンド ID は、1 つまたは複数のメニューで、framework がユーザー定義のツールを挿入する場所の場所をマークします。

確保あります一連の Id をユーザー定義のツールを表す文字列テーブルにします。 予約する文字列の数は、ユーザーを定義するユーザー ツールの最大数です。 次の例では、これらの名前は`ID_USER_TOOL1`を通じて`ID_USER_TOOL10`します。

提案をツールとして呼び出される外部プログラムのディレクトリおよび引数を選択するためにユーザーに提供できます。 これを行うには、リソース エディターで 2 つのポップアップ メニューを作成します。 次の例でこれらの名前は`IDR_MENU_ARGS`と`IDR_MENU_DIRS`します。 これらのメニューで、各コマンドには、アプリケーションの文字列テーブルに文字列を定義します。 文字列のリソース ID は、コマンド ID と一致する必要があります。

派生クラスを作成することもできます。 [CUserTool クラス](../mfc/reference/cusertool-class.md)既定の実装を置き換えます。 これを行うには、対象となるのではなく、CWinAppEx::EnableUserTools の 4 番目のパラメーターとして、派生クラスのランタイム情報を渡す ([CUserTool クラス](../mfc/reference/cusertool-class.md))。

適切な定数を定義した後で呼び出す[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)ユーザー定義のツールを有効にします。

次のメソッド呼び出しでは、これらの定数を使用する方法を示します。

[!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/cpp/user-defined-tools_1.cpp)]

ツール タブの収録、この例では、**カスタマイズ** ダイアログ ボックス。 フレームワークはコマンド ID と一致するコマンドを置き換えます`ID_TOOLS_ENTRY`でユーザーがそのメニューを開くたびに現在定義されているユーザー ツールのセットで任意のメニュー。 コマンド Id`ID_USER_TOOL1`を通じて`ID_USER_TOOL10`ユーザー定義のツールを使用するために予約されています。 クラスは、 [CUserTool クラス](../mfc/reference/cusertool-class.md)ユーザー ツールの呼び出しを処理します。 [ツール] タブ、**カスタマイズ**ダイアログ ボックスには、メニューにアクセスする引数とディレクトリのエントリ フィールドの右側にあるボタン**IDR_MENU_ARGS**と**IDR_MENU_DIRS**.適切なテキスト ボックスに追加しますフレームワークが、コマンド ID に等しいリソース ID を持つ文字列を使用するときに、ユーザーは、これらのメニューのいずれかからコマンドを選択します。

### <a name="including-predefined-tools"></a>定義済みのツールを含む

オーバーライドする必要がある、アプリケーションの起動時に一部のツールを事前に定義する場合、 [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)アプリケーションのメイン ウィンドウのメソッド。 メソッドには、次の手順を実行する必要があります。

##### <a name="to-add-new-tools-in-loadframe"></a>LoadFrame で新しいツールを追加するには

1. ポインターを取得、 [CUserToolsManager クラス](../mfc/reference/cusertoolsmanager-class.md)オブジェクトを呼び出すことによって[CWinAppEx::GetUserToolsManager](../mfc/reference/cwinappex-class.md#getusertoolsmanager)します。

1. 作成するすべてのツールを呼び出す[CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool)します。 このメソッドへのポインターを返します、 [CUserTool クラス](../mfc/reference/cusertool-class.md)オブジェクトし、ツールの内部コレクションに新しく作成したユーザー ツールを追加します。 派生クラスのランタイム情報を指定したかどうかは[CUserTool クラス](../mfc/reference/cusertool-class.md)の 4 番目のパラメーターとして[CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools)、 [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool)をインスタンス化され、代わりにそのクラスのインスタンスが返されます。

1. 設定してそのテキスト ラベルを設定、各ツールの`CUserTool::m_strLabel`のコマンドを呼び出すことによって設定および`CUserTool::SetCommand`します。 既定の実装[CUserTool クラス](../mfc/reference/cusertool-class.md)への呼び出しで指定されているプログラムから使用可能なアイコンを自動的に取得`SetCommand`します。

## <a name="see-also"></a>関連項目

[MFC のカスタマイズ](../mfc/customization-for-mfc.md)<br/>
[CUserTool クラス](../mfc/reference/cusertool-class.md)<br/>
[CUserToolsManager クラス](../mfc/reference/cusertoolsmanager-class.md)<br/>
[CWinAppEx クラス](../mfc/reference/cwinappex-class.md)
