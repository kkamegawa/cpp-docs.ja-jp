---
title: /CETCOMPAT (制御フローの強制テクノロジ互換)
ms.date: 02/01/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 3adb147804674b52a5d77030c48567ec04da6aa6
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703465"
---
# <a name="cetcompat-control-flow-enforcement-technology-compatible"></a>/CETCOMPAT (制御フローの強制テクノロジ互換)

制御フローの適用テクノロジ (CET) と互換性のある実行可能ファイルの画像をマークするかどうかを指定します。

## <a name="syntax"></a>構文

> **/CETCOMPAT**\[**:NO**]

## <a name="arguments"></a>引数

**違います**<br/>
Executalbe マークしないで中央ヨーロッパ標準時との互換性を指定します。

## <a name="remarks"></a>Remarks

制御フローの適用テクノロジ (CET) は、特定の種類のマルウェアによる攻撃を防御する機能を提供するコンピューターのプロセッサ機能です。 詳細については、次を参照してください。 [Intel 制御フローの適用テクノロジ プレビュー](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf)します。

**/CETCOMPAT**リンカー オプション、リンカーは中央ヨーロッパ標準時と互換性のあるとしてバイナリをマークします。 **/CETCOMPAT:NO**として CET と互換性のないバイナリをマークします。 両方のオプションをコマンドラインで指定する場合は、指定された最後の 1 つが使用されます。 このスイッチは、現在 x86 および x64 アーキテクチャに適用できるのみです。

**/CETCOMPAT**オプションは、以降、Visual Studio 2019 の Preview 3 のツールセットで使用できます。

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Visual Studio で/CETCOMPAT リンカー オプションを設定するには

1. 開く、**プロパティ ページ**プロジェクトのダイアログ ボックス。 詳細については、「[プロジェクト プロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. **追加オプション**ボックスで、追加 **/CETCOMPAT**または **/CETCOMPAT:NO**選び、 **OK**または**適用**、変更を保存します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- このオプションでは、同等のプログラムはありません。

## <a name="see-also"></a>関連項目

[リンカー オプションの設定](../../build/reference/setting-linker-options.md)<br/>
[リンカー オプション](../../build/reference/linker-options.md)
