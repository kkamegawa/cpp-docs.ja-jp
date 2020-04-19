---
title: /RTC (ランタイム エラー チェック)
ms.date: 11/04/2016
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
helpviewer_keywords:
- /RTCs compiler option [C++]
- -RTC1 compiler option [C++]
- run-time errors, error checks
- -RTCu compiler option [C++]
- /RTC1 compiler option [C++]
- /RTCc compiler option [C++]
- /RTCu compiler option [C++]
- __MSVC_RUNTIME_CHECKS macro
- -RTCs compiler option [C++]
- RTCs compiler option
- RTC1 compiler option
- run-time errors, run-time checks
- run-time checks, /RTC option
- RTCu compiler option
- RTCc compiler option
- -RTCc compiler option [C++]
ms.assetid: 9702c558-412c-4004-acd5-80761f589368
ms.openlocfilehash: a830ff5b8ba4b7fcd95eb462f899f2eadce6de11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318551"
---
# <a name="rtc-run-time-error-checks"></a>/RTC (ランタイム エラー チェック)

組み合わせて、実行時エラー チェック機能を無効にするために使用、 [runtime_checks](../../preprocessor/runtime-checks.md)プラグマ。

## <a name="syntax"></a>構文

```
/RTC1
/RTCc
/RTCs
/RTCu
```

## <a name="arguments"></a>引数

**1**<br/>
等価の **/RTC**`su`します。

**c**<br/>
レポートの値は、小さいデータ型とデータが失われる結果に割り当てられます。 たとえば、値型の場合`short 0x101`型の変数に割り当てられている`char`します。

このオプションを切り捨てを予定して、たとえば、最初の 8 ビットの場合の状況を報告する、`int`として返されます、`char`します。 **/RTC** `c` 、実行時エラーが発生の結果として、実行時エラーを回避するために必要な情報をマスクすることができます、情報が代入の結果として失われた場合は、 **/RTC** `c`. 例:

```
#include <crtdbg.h>

char get8bits(int value, int position) {
   _ASSERT(position < 32);
   return (char)(value >> position);
   // Try the following line instead:
   // return (char)((value >> position) & 0xff);
}

int main() {
   get8bits(12341235,3);
}
```

**s**<br/>
スタック フレーム ランタイム エラー チェック、次のようを有効にします。

- ローカル変数を 0 以外の値を初期化します。 これにより、デバッグ モードで実行されているときに表示されないバグを特定できます。 スタックの変数では、リリース ビルドで変数をスタックのコンパイラの最適化のため、リリース ビルドと比べると、デバッグ ビルドでの 0 になりますが、大きい可能性はあります。 プログラムが使用されると、スタックの領域、ことはありません 0 にリセットして、コンパイラによって、されます。 そのため、同じスタック領域を使用して処理を行う、以降の初期化されていないスタック変数では、スタック メモリで以前使用から残された値を返すことができます。

- オーバーランや配列などのローカル変数のアンダーランを検出します。 **/RTC** `s`コンパイラ埋め込み構造体からの結果をメモリにアクセスするときにオーバーランが検出されません。 使用して埋め込みが発生する可能性が[align](../../cpp/align-cpp.md)、 [/Zp (構造体メンバーの配置)](zp-struct-member-alignment.md)、または[パック](../../preprocessor/pack.md)余白を追加するコンパイラが必要な方法で構造体の要素を注文する場合またはします。

- スタック ポインターの検証は、スタック ポインターの破損を検出します。 スタック ポインターの破損は、呼び出し規約の不一致によることができます。 エクスポートされた DLL で関数を呼び出す関数ポインターを使用して、たとえば、 [_ _stdcall](../../cpp/stdcall.md)として関数へのポインターを宣言するが、 [_ _cdecl](../../cpp/cdecl.md)します。

**u**<br/>
レポートが割り当てられていない変数を使用するとします。 たとえば、生成する命令`C4701`下で実行時エラーが生成される場合も **/RTC**`u`します。 任意の命令を生成する[コンパイラの警告 (レベル 1 およびレベル 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)下で実行時エラーが生成される **/RTC**`u`します。

ただし、次のコード フラグメントを検討してください。

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

変数が初期化されている可能性がありますが場合に、報告されませんによって実行時に **/RTC**`u`します。 たとえば、変数がエイリアス化されたポインターを通じてと、コンパイラいない変数を追跡を初期化されていない使用を報告します。 実際には、そのアドレスを取得して、変数を初期化できます。 (& A) このような状況で、代入演算子と同様に演算子の動作。

## <a name="remarks"></a>Remarks

実行時エラー チェックは、実行中のコードで問題を検出する方法です。詳細については、次を参照してください。[方法。ネイティブ ランタイム チェックを使用する](/visualstudio/debugger/how-to-use-native-run-time-checks)」を参照してください。

いずれかを使用してコマンドラインでプログラムをコンパイルする場合、 **/RTC**コンパイラ オプション、すべてのプラグマ[最適化](../../preprocessor/optimize.md)手順については、コードでは失敗します。 実行時エラー チェックが有効で (最適化) リリース ビルドではないためにです。

使用する必要があります **/RTC**開発ビルドで **/RTC**製品版をビルドしない使用する必要があります。 **/RTC**コンパイラの最適化では使用できません ([/O オプション (コードの最適化)](o-options-optimize-code.md))。 ビルドされたプログラム イメージ **/RTC**若干大きくなりでビルドされたイメージよりもわずかに遅くなります **/Od** (最大 5% よりも低速、 **/Od**ビルド)。

いずれかを使用すると、_ _msvc_runtime_checks プリプロセッサ ディレクティブが定義される **/RTC**オプションまたは[/GZ](gz-enable-stack-frame-run-time-error-checking.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. をクリックして、**コード生成**プロパティ ページ。

1. 次のプロパティの一方または両方を変更します。**基本ランタイム チェック**または**チェックを小さい型**します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> プロパティおよび <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A> プロパティを参照してください。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[方法: ネイティブ ランタイム チェックを使用する](/visualstudio/debugger/how-to-use-native-run-time-checks)
