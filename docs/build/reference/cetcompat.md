---
title: /CETCOMPAT (CET シャドウ スタック互換)
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 0ed5d9d4f9f4f4dc5cd4fc19df4179e86e430187
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273249"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/CETCOMPAT (CET シャドウ スタック互換)

制御フローの適用テクノロジ (CET) シャドウ スタックに互換性がある実行可能イメージをマークするかどうかを指定します。

## <a name="syntax"></a>構文

> **/CETCOMPAT**\[**:NO**]

## <a name="arguments"></a>引数

**違います**<br/>
実行可能ファイル マークしないで CET シャドウ スタックとの互換性を指定します。

## <a name="remarks"></a>Remarks

制御フローの適用テクノロジ (CET) シャドウ スタックは、戻り指向プログラミング (ROP) に対する防御機能ベースのマルウェアの攻撃を提供するコンピューターのプロセッサ機能です。 詳細については、次を参照してください。 [Intel 制御フローの適用テクノロジ プレビュー](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf)します。

**/CETCOMPAT**リンカー オプションとして CET シャドウ スタックと互換性のあるバイナリをマークするリンカーに指示します。 **/CETCOMPAT:NO**として CET シャドウ スタックと互換性のないバイナリをマークします。 両方のオプションをコマンドラインで指定する場合は、指定された最後の 1 つが使用されます。 このスイッチは、現在 x86 および x64 アーキテクチャに適用できるのみです。

**/CETCOMPAT**オプションは、以降、Visual Studio 2019 の Preview 3 のツールセットで使用できます。

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Visual Studio で/CETCOMPAT リンカー オプションを設定するには

1. 開く、**プロパティ ページ**プロジェクトのダイアログ ボックス。 詳細については、「[プロジェクト プロパティの操作](../working-with-project-properties.md)」を参照してください。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. **追加オプション**ボックスで、追加 **/CETCOMPAT**または **/CETCOMPAT:NO**選び、 **OK**または**適用**、変更を保存します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

このオプションでは、同等のプログラムはありません。

## <a name="see-also"></a>関連項目

[リンカー オプション](linker-options.md)
