---
title: /Zp (構造体メンバーの配置)
ms.date: 04/04/2019
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
ms.openlocfilehash: d76cd93c7af4228bff8f73fa3bcbf40fa149b0be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315912"
---
# <a name="zp-struct-member-alignment"></a>/Zp (構造体メンバーの配置)

メモリに構造体のメンバーをパックする方法を制御し、モジュール内のすべての構造の同じパッキングを指定します。

## <a name="syntax"></a>構文

> **/Zp**[**1**|**2**|**4**|**8**|**16**]

## <a name="remarks"></a>Remarks

**/Zp**_n_オプションは各構造体メンバーを格納する場所をコンパイラに指示します。 コンパイラはメンバーの種類のサイズのどちらか小さい方である境界を 1 つ目の後にメンバーを格納または*n*-バイト境界。

パッキングの使用可能な値は、次の表で説明します。

|/Zp 引数|効果|
|-|-|
|1|構造体は、1 バイト境界でパックします。 同じ **/Zp**します。|
|2|構造体を 2 バイト境界でパックします。|
|4|構造体は、4 バイト境界でパックします。|
|8|8 バイト境界 (x86、ARM、および ARM64 の既定値) の構造体にパックします。|
|16| 16 バイト境界 (x64 用の既定値) の構造体にパックします。|

特定のアラインメント要件がない限り、このオプションを使用しないでください。

> [!WARNING]
> Windows SDK の C++ ヘッダーが設定され、想定 **、/zp8 です**梱包を内部的にします。 メモリの破損が生じる場合、 **/Zp** Windows SDK のヘッダー内で設定を変更します。 ヘッダーは、いずれかが影響を受けません **/Zp**オプションをコマンドラインで設定します。

使用することも[パック](../../preprocessor/pack.md)制御構造のパッキングにします。 アラインメントの詳細については、次のトピックを参照してください。

- [align](../../cpp/align-cpp.md)

- [__alignof 演算子](../../cpp/alignof-operator.md)

- [__unaligned](../../cpp/unaligned.md)

- [/ALIGN (セクションの配置)](align-section-alignment.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **コード生成**プロパティ ページ。

1. 変更、**構造体メンバーのアラインメント**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md) \
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
