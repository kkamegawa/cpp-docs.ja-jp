---
title: ダイアログ エディター (C++) のトラブルシューティング
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 21882868-5ac4-4a41-a4a6-eaaa059402ea
ms.openlocfilehash: fe0fe704b5c17d0db4e3419f29d21f0e60bc4211
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484956"
---
# <a name="troubleshooting-the-dialog-editor-c"></a>ダイアログ エディター (C++) のトラブルシューティング

マネージ プロジェクトにリソースを追加する方法については、次を参照してください。 [Resources in Desktop Apps](/dotnet/framework/resources/index)で、 *.NET Framework 開発者ガイド*します。 マネージ プロジェクトにリソース ファイルを手動で追加、リソースへのアクセス、静的リソースの表示方法、およびリソース文字列のプロパティを割り当てる方法については、次を参照してください。[デスクトップ アプリのリソース ファイルの作成](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)です。 管理対象アプリ内のリソースのグローバリゼーションとローカリゼーションについては、次を参照してください。 [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index)します。

うちおく必要がある、C で作業するとき、いくつかの問題を以下に示します**ダイアログ**エディター。

## <a name="adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function"></a>ダイアログにコントロールを追加すると、ダイアログ ボックスを不要になった関数

ダイアログ ボックスに、一般的なコントロールまたはリッチ エディット コントロールを追加すると、ダイアログ ボックスのテストまたはダイアログ自体は表示されないときに表示されません。

### <a name="example-of-the-problem"></a>問題の例

1. Windows アプリケーション (コンソール アプリケーションではなく) を作成するためにアプリケーション設定を変更する、Win32 プロジェクトを作成します。

1. [リソース ビュー](../windows/resource-view-window.md)、.rc ファイルをダブルクリックします。

1. ダイアログ オプションで、をダブルクリック、**について**ボックス。

1. 追加、 **IP アドレス コントロール** ダイアログ ボックス。

1. 保存と**すべてリビルド**します。

1. プログラムを実行します。

1. ダイアログ ボックスの**ヘルプ** メニューのをクリックして、**について**コマンド; ダイアログ ボックスが表示されます。

### <a name="the-cause"></a>原因

現時点では、**ダイアログ**エディターは、自動的に、リッチ エディット コントロールをダイアログ ボックスにドラッグ アンド ドロップ、次の一般的なコントロールまたはときに、プロジェクトにコードを追加しません。 Visual Studio はエラーまたは警告がこの問題が発生します。 を解決するには、コントロールのコードを手動で追加します。

||||
|-|-|-|
|スライダー コントロール|ツリー コントロール|Date Time Picker|
|スピン コントロール|タブ コントロール|月間予定表|
|プログレス コントロール|アニメーション コントロール|IP アドレスの管理|
|ホット キー|リッチ エディット コントロール|拡張コンボ ボックス|
|リスト コントロール|リッチ エディット 2.0 コントロール|カスタム コントロール|

### <a name="fix-for-common-controls"></a>コントロールの一般的な問題を修正しました

コモン コントロール ダイアログ ボックスを使用するにを呼び出す必要があります[InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex)または`AFXInitCommonControls` ダイアログ ボックスを作成する前にします。

### <a name="fix-for-richedit-controls"></a>リッチ エディット コントロールの修正

呼び出す必要があります`LoadLibrary`リッチ エディット コントロールの。 詳細については、次を参照してください。[リッチのエディット コントロールについて](/windows/desktop/Controls/about-rich-edit-controls)Windows sdk と[リッチ エディット コントロールの概要](../mfc/overview-of-the-rich-edit-control.md)します。

### <a name="requirements"></a>必要条件

Win32

## <a name="using-the-richedit-10-control-with-mfc"></a>MFC でのリッチ エディット 1.0 コントロールの使用

リッチ エディット コントロールを使用するには、まず[AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2)リッチ エディット 2.0 コントロール (RICHED20 を読み込めません。DLL)、または呼び出す[AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)古い RichEdit 1.0 コントロール (RICHED32 を読み込めません。DLL) です。

現在を使用することが[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)古い RichEdit 1.0 コントロールでは、クラスが`CRichEditCtrl`はリッチ エディット 2.0 コントロールをサポートするためにのみ設計されています。 リッチ エディット 1.0 とリッチ エディット 2.0 は似ていますが、ため、ほとんどのメソッドは機能します。 ただしの 1.0 と 2.0 のコントロールをいくつかのメソッドが正常に動作しない可能性がありますまたはまったく動作しないようにいくつかの違いに注意してください。

### <a name="requirements"></a>必要条件

MFC

## <a name="see-also"></a>関連項目

[ダイアログ エディター](../windows/dialog-editor.md)