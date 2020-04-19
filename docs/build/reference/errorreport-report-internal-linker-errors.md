---
title: /ERRORREPORT (内部リンカー エラーの報告)
description: Microsoft NMAKE のコマンドラインオプションのリファレンスガイドです。
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
ms.openlocfilehash: 5e919d4f7eb59524b9145c8e3e59613e60aef1d2
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257690"
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (内部リンカー エラーの報告)

**/Errorreport**オプションは非推奨とされます。 Windows Vista 以降では、エラー報告は[Windows エラー報告 (WER)](/windows/win32/wer/windows-error-reporting)設定によって制御されます。

## <a name="syntax"></a>構文

> **/Errorreport:** \[ **none** \| **prompt** \| **queue** \| **send** ]

## <a name="remarks"></a>コメント

**/Errorreport**引数は、Windows エラー報告サービスの設定によってオーバーライドされます。 レポートが Windows エラー報告によって有効になっている場合、リンカーは内部エラーのレポートを Microsoft に自動的に送信します。 Windows エラー報告で無効になっている場合、レポートは送信されません。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳しくは、「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](../working-with-project-properties.md)」をご覧ください。

1. **[構成プロパティ]**  > [**リンカー** > **詳細設定**] プロパティページを開きます。

1. **エラー報告**のプロパティを変更します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- [https://docs.microsoft.com/azure/active-directory/develop/scenario-protected-web-api-overview](<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>) をご覧ください。

## <a name="see-also"></a>参照

[MSVC リンカーリファレンス](linking.md)\
[MSVC リンカーオプション](linker-options.md)
