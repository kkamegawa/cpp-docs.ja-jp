---
title: /FILEALIGN (ファイルのセクションの配置)
ms.date: 10/23/2017
f1_keywords:
- /filealign
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
ms.openlocfilehash: 43cfdd6efb163013d05877e91c8375eb592295a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271152"
---
# <a name="filealign-align-sections-in-files"></a>/FILEALIGN (ファイルのセクションの配置)

**/FILEALIGN**リンカー オプションを使用して、指定のサイズの倍数として、出力ファイルに書き込まれるセクションの配置を指定できます。

## <a name="syntax"></a>構文

> __/FILEALIGN:__*サイズ*

### <a name="parameters"></a>パラメーター

*size*<br/>
2 の累乗である必要があります (バイト) セクションの配置のサイズ。

## <a name="remarks"></a>Remarks

**/FILEALIGN**整列の倍数である境界上の出力ファイル内の各セクションをリンカーにオプション、*サイズ*値。 既定では、リンカーは、固定の配置のサイズを使用しません。

**/FILEALIGN**オプションは、ディスク使用率をより効率的に使用できますか、ページをディスクから読み込みます高速化します。 セクションのサイズを小さくはまたはのダウンロード サイズを小さく小型のデバイスで実行されるアプリの便利な可能性があります。 ディスク上のセクションの配置では、メモリ内の配置は影響しません。

出力ファイル内のセクションに関する情報を表示するには、[DUMPBIN](dumpbin-reference.md) を使用します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**コマンドライン**プロパティ ページで、**リンカー**フォルダー。

1. オプション名を入力 **/FILEALIGN:** およびサイズ、**追加オプション**ボックス。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
