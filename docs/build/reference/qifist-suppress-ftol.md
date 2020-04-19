---
title: /QIfist (_ftol を呼び出さない)
ms.date: 11/04/2016
f1_keywords:
- /qifist
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
ms.openlocfilehash: 7af88c91793688d23cf35177ae7a5250b04832a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319292"
---
# <a name="qifist-suppress-ftol"></a>/QIfist (_ftol を呼び出さない)

非推奨。 浮動小数点型から整数型への変換が必要なときには、ヘルパー関数 `_ftol` を呼び出しません。

## <a name="syntax"></a>構文

```
/QIfist
```

## <a name="remarks"></a>Remarks

> [!NOTE]
>  **/Qifist**でのみ使用 x86 を対象とするコンパイラこのコンパイラ オプションでは使用できません x64 を対象とするコンパイラや arm に対応します。

`_ftol` 関数では、浮動小数点型から整数型への変換に加えて、浮動小数点制御ワードのビット 10 と 11 を設定して、FPU (Floating-Point Unit) の丸めモードをゼロ (切り捨て) にします。 したがって、浮動小数点型から整数型への変換は、ANSI C 規格どおりに行われ、小数部分を破棄することが保証されます。 使用する場合 **/QIfist** 、この保証が適用されなくなった。 丸めモードは、Intel 社のリファレンス マニュアルに示されたとおり、次の 4 とおりのうちのいずれかになります。

- 一番近い値に丸める (中間の場合は偶数)。

- 負の無限大に丸める。

- 正の無限大に丸める。

- ゼロに丸める。

使用することができます、 [_control87、_controlfp、 \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C ランタイム関数、FPU の丸め動作を変更します。 FPU の既定の丸めモードでは、一番近い値に丸められます。 使用して **/QIfist**リスクが伴いますが、アプリケーションのパフォーマンスを向上させることができます。 ビルドされたコードを使用する前に、丸めモードと小文字を区別する、コードの部分を徹底的にテストする必要があります **/QIfist**実稼働環境でします。

[/arch (x86)](arch-x86.md)と **/QIfist**同じコンパイル単位で使用することはできません。

> [!NOTE]
>  **/Qifist**が有効で既定ではビットの丸め処理も浮動小数点から浮動小数点に影響するため指していない丸め処理を行う (これが発生したすべての計算後) ため、C スタイル (ゼロ) の方向に丸め処理のフラグを設定すると、浮動小数点計算が異なる可能性があります。 **/Qifist**浮動小数点数の小数部の切り捨てについて予想される動作にコードが依存している場合は使用する必要があります。 不明な場合は使用しないで **/QIfist**します。

**/QIfist**オプションは Visual Studio 2005 以降で非推奨とされます。 浮動小数点型から整数型への変換処理の速度が飛躍的に向上しました。 非推奨のコンパイラ オプションの一覧は、次を参照してください。**非推奨とされた削除済みのコンパイラ オプション**で[Compiler Options Listed by Category](compiler-options-listed-by-category.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[/Q オプション (低水準の操作)](q-options-low-level-operations.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
