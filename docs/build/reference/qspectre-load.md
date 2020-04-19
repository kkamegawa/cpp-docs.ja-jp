---
title: /Qspectre-load
description: Microsoft C/C++コンパイラ (MSVC)/Qspectre-load オプションについて説明します。
ms.date: 01/28/2020
helpviewer_keywords:
- /Qspectre-load
ms.openlocfilehash: a766cf9b7eef11b7c5819cbdaa7706ab5b80c608
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035554"
---
# <a name="qspectre-load"></a>/Qspectre-load

すべての読み込み命令のシリアル化命令のコンパイラ生成を指定します。 このオプションにより、 **/Qspectre**フラグが拡張され、負荷に基づいて予測**実行のサイドチャネル攻撃**が発生する可能性が軽減されます。

## <a name="syntax"></a>構文

> **/Qspectre-load**

## <a name="remarks"></a>コメント

**/Qspectre-load**により、コンパイラはメモリからの読み込みを検出し、その後にシリアル化命令を挿入します。 `RET` や `CALL`を含むメモリを読み込む制御フロー命令は、負荷と制御フロー転送に分割されます。 負荷が保護されていることを確認するために、読み込みの後に `LFENCE` が続きます。 コンパイラが制御フロー命令 (`jmp` 命令など) を分割できない場合は、代替の軽減策を使用します。 たとえば、次に示すように、コンパイラは、LFENCE を挿入する前にターゲットを非破壊的な方法で読み込むように命令を追加することで、`jmp [rax]` を軽減します。

```asm
    xor rbx, [rax]
    xor rbx, [rax]  ; force a load of [rax]
    lfence          ; followed by an LFENCE
    jmp [rax]
```

**/Qspectre-load**はすべての負荷の推測を停止するため、パフォーマンスへの影響は高くなります。 この軽減策は、どこにも適していません。 保護を必要としないパフォーマンスクリティカルなコードブロックがある場合は、`__declspec(spectre(nomitigation))`を使用してこれらの軽減策を無効にすることができます。 詳細については、「 [__declspec spectre](../../cpp/spectre.md)」を参照してください。

**/Qspectre-load**オプションは、既定ではオフになっており、すべての最適化レベルをサポートしています。

**/Qspectre-load**オプションは、Visual Studio 2019 バージョン16.5 以降で使用できます。 このオプションは、x86 および x64 プロセッサを対象とするコンパイラでのみ使用できます。 ARM プロセッサを対象とするコンパイラでは使用できません。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関する記事を参照してください。

2. **[構成プロパティ]**  > [ **CC++ /**  > **コード生成**] プロパティページを選択します。

3. **Spectre 軽減**プロパティの新しい値を選択します。 **[OK]** を選択して変更を適用します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>参照

[/Q オプション (低レベルの操作)](q-options-low-level-operations.md)\
[MSVC コンパイラオプション](compiler-options.md)\
[MSVC コンパイラのコマンドライン構文](compiler-command-line-syntax.md)
