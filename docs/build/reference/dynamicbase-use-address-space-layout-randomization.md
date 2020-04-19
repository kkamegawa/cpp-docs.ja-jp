---
title: /DYNAMICBASE (ASLR (Address Space Layout Randomization) の使用)
ms.date: 06/12/2018
f1_keywords:
- VC.Project.VCLinkerTool.RandomizedBaseAddress
helpviewer_keywords:
- -DYNAMICBASE linker option
- /DYNAMICBASE linker option
- DYNAMICBASE linker option
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
ms.openlocfilehash: a3495de3ec72bcac78cdee2f5f3265864e7a2932
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293070"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (ASLR (Address Space Layout Randomization) の使用)

ランダムに再ベースできる読み込み時に Windows Vista で初めて提供された Windows のアドレス空間レイアウト randomization (ASLR) 機能を使用して実行可能イメージを生成するかどうかを指定します。

## <a name="syntax"></a>構文

> **/DYNAMICBASE** **[:NO]**

## <a name="remarks"></a>Remarks

**/DYNAMICBASE**オプションのヘッダーを変更する、*実行可能イメージ*、.dll または .exe ファイルをアプリケーションが、読み込み時にランダムにリベースする必要があり、仮想アドレスが有効かどうかを示すためにヒープの仮想メモリの場所に影響を与える割り当てのランダム化スタック、およびその他のオペレーティング システムの割り当て。 **/DYNAMICBASE**オプションは、32 ビットと 64 ビットの両方のイメージに適用されます。 ASLR は、Windows Vista およびそれ以降のオペレーティング システムでサポートされます。 オプションは、以前のオペレーティング システムによって無視されます。

既定では、 **/DYNAMICBASE**を有効にします。 このオプションを無効にするには、 **/DYNAMICBASE:NO**します。 **/DYNAMICBASE**オプションが必要です、 [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)オプションに影響を与えます。

### <a name="to-set-this-linker-option-in-visual-studio"></a>このリンカー オプションを Visual Studio で設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **詳細**プロパティ ページ。

1. 変更、**ランダム化されたベース アドレス**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>

## <a name="see-also"></a>関連項目

- [MSVC リンカーのリファレンス](linking.md)
- [MSVC リンカー オプション](linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Windows ISV Software Security Defenses](https://msdn.microsoft.com/library/bb430720.aspx)