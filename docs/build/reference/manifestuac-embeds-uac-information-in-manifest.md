---
title: /MANIFESTUAC (UAC 情報をマニフェストに組み込む)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
ms.openlocfilehash: ecc30baabdcb60a030418e9643e2fcffe5ba8281
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321372"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC (UAC 情報をマニフェストに組み込む)

ユーザー アカウント制御 (UAC) 情報をプログラム マニフェストに組み込むかどうかを指定します。

## <a name="syntax"></a>構文

```
/MANIFESTUAC
/MANIFESTUAC:NO
/MANIFESTUAC:fragment
/MANIFESTUAC:level=_level
/MANIFESTUAC:uiAccess=_uiAccess
```

### <a name="parameters"></a>パラメーター

*フラグメント*<br/>
`level` 値および `uiAccess` 値を格納する文字列。 詳細については、このトピックで後述する「解説」を参照してください。

*_level*<br/>
いずれかの*asInvoker*、 *highestAvailable*、または*requireAdministrator*します。 既定値は asInvoker です。 詳細については、このトピックで後述する「解説」を参照してください。

*_uiAccess*<br/>
**true**する場合は、アプリケーションをユーザー インターフェイスの保護レベルをバイパスし、上位の権限の windows デスクトップへの入力。 それ以外のドライブ**false**します。 既定値は**false**します。 設定**true**ユーザー インターフェイスのユーザー補助アプリケーションに対してのみです。

## <a name="remarks"></a>Remarks

コマンド ラインで複数の /MANIFESTUAC オプションを指定した場合は、最後に入力したオプションが優先されます。

/MANIFESTUAC:level に指定できるのは、次のとおりです。

- `asInvoker`:アプリケーションは、それを開始したプロセスと同じアクセス許可で実行されます。 アプリケーションを選択してより高いアクセス許可レベルに昇格させることができます**管理者として実行**します。

- highestAvailable:アプリケーションは、可能な高い権限レベルで実行されます。 アプリケーションを開始するユーザーが管理者グループのメンバーである場合、このオプションは requireAdministrator と同じです。 使用可能な最も高いアクセス許可レベルが、開始したプロセスのレベルより高い場合は、資格情報の入力が求められます。

- requireAdministrator:アプリケーションは、管理者のアクセス許可で実行されます。 アプリケーションを開始するユーザーは、管理者グループのメンバーである必要があります。 開始したプロセスが管理者のアクセス許可で実行されない場合は、資格情報の入力が求められます。

/MANIFESTUAC:fragment オプションを使用することにより、level 値と uiAccess 値の指定を 1 ステップで行うことができます。 fragment は、次の形式で指定します。

```
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[構成プロパティ]** ノードを展開します。

1. 展開、**リンカー**ノード。

1. 選択、**マニフェスト ファイル**プロパティ ページ。

1. 変更、**を有効にするユーザー アカウント制御 (UAC)**、 **UAC の実行レベル**、および**UAC による UI 保護のバイパス**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A>、および <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A> を参照してください。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
