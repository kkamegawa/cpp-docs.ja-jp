---
title: /Qspectre-load-cf
description: Microsoft C/C++コンパイラ (MSVC)/Qspectre-load-cf オプションについて説明します。
ms.date: 01/28/2020
helpviewer_keywords:
- /Qspectre-load-cf
no-loc:
- Qspectre-load-cf
ms.openlocfilehash: c32b843df517cb6fbe662fba0b592cbf745f1764
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035548"
---
# /Qspectre-load-cf

読み込みを含むすべての制御フロー命令のシリアル化命令のコンパイラ生成を指定します。 このオプションは、 [/Qspectre-load](qspectre-load.md)オプションによって実行される軽減策のサブセットを実行します。

## <a name="syntax"></a>構文

> **/Qspectre-load-cf**

## <a name="remarks"></a>コメント

**/Qspectre-load-cf** により、コンパイラは、メモリから読み込まれる `JMP`、`RET`、および `CALL` 制御フロー命令を検出し、読み込み後にシリアル化命令を挿入します。 可能であれば、これらの手順は負荷と制御フロー転送に分割されます。 負荷が保護されていることを確認するために、読み込みの後に `LFENCE` が続きます。 コンパイラが命令を分割できない場合があります (`JMP` 命令など)。そのため、代替の軽減策が使用されます。 たとえば、次に示すように、コンパイラは、LFENCE を挿入する前にターゲットを非破壊的な方法で読み込むように命令を追加することで、`jmp [rax]` を軽減します。

```asm
    xor rbx, [rax]
    xor rbx, [rax]  ; force a load of [rax]
    lfence          ; followed by an LFENCE
    jmp [rax]
```

**/Qspectre-load-cf** は制御フロー命令のすべての負荷の推測を停止するため、パフォーマンスへの影響は高くなります。 この軽減策は、どこにも適していません。 保護を必要としないパフォーマンスクリティカルなコードブロックがある場合は、`__declspec(spectre(nomitigation))`を使用してこれらの軽減策を無効にすることができます。

**/Qspectre-load-cf** オプションは既定でオフになっており、すべての最適化レベルをサポートしています。

**/Qspectre-load-cf** オプションは、Visual Studio 2019 バージョン16.5 以降で使用できます。 このオプションは、x86 および x64 プロセッサを対象とするコンパイラでのみ使用できます。 ARM プロセッサを対象とするコンパイラでは使用できません。

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
