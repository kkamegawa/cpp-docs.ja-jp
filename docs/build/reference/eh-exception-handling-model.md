---
title: /EH (例外処理モデル)
ms.date: 08/14/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 9f5eed60ecb51abc1d8fbd3c38773bbf782b23a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271802"
---
# <a name="eh-exception-handling-model"></a>/EH (例外処理モデル)

コンパイラで使用される例外処理の種類、例外チェックを最適化して除去するタイミング、および例外が原因でスコープを外れた C++ オブジェクトを破棄するかどうかを指定します。 場合 **/EH**が指定されていない、コンパイラにより、コードは非同期構造化例外と C++ の例外の両方をキャッチできますを非同期例外のためのスコープを外れた C++ オブジェクトを破棄しません。

## <a name="syntax"></a>構文

> **/EH**{**s**|**a**} **[c]** **[r]** [ **-** ]

## <a name="arguments"></a>引数

**a**<br/>
非同期の両方をキャッチする例外処理モデル (構造化) と c++ を使用して同期 (C++) 例外`catch(...)`構文。

**s**<br/>
例外処理モデルを同期 (C++) 例外のみをキャッチし、コンパイラとして宣言された関数を想定する**extern"C"** 例外をスローする可能性があります。

**c**<br/>
使用されている場合**s** ( **/EHsc**)、C++ 例外のみをキャッチし、コンパイラとして宣言された関数を想定する**extern"C"** C++ 例外はスローされません。 **/EHca** は **/EHa**と同じです。

**r**<br/>
すべてのランタイム終了チェックを常に生成するコンパイラに指示**noexcept**関数。 既定では、ランタイムのチェックの**noexcept**コンパイラ関数がのみ非スロー関数を呼び出すと判断した場合は、すぐ最適化可能性があります。

## <a name="remarks"></a>Remarks

**/EHa** コンパイラ オプションは、ネイティブ C++ `catch(...)` 句で非同期構造化例外処理 (SEH) をサポートするために使用されます。 指定せずに SEH を実装する **/EHa**、使用することが、 **__try**、 **__except**、および **__finally**構文。 Windows および Visual C++ は SEH をサポートしていますが、ISO 標準の C++ 例外処理 ( **/EHs** または **/EHsc**) の方がコードの移植性と柔軟性に優れているため、こちらの例外処理を使用することを強くお勧めします。 ただし、既存のコードで、または特定の種類のプログラムの — など、共通言語ランタイムをサポートするためにコンパイルされたコードで ([/clr (共通言語ランタイムのコンパイル)](clr-common-language-runtime-compilation.md))-SEH を使用する必要があります。 詳細については、「 [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)」を参照してください。

**/EHa** を指定し、 `catch(...)` を使用してすべての例外を処理しようとするのは危険です。 非同期例外のほとんどが回復不能で、致命的であると見なされます。 こうした例外をキャッチして操作を続行すると、プロセスが破損し、検出して修正するのが難しいバグが発生する可能性があります。

**/EHs** または **/EHsc**を使用すると、 `catch(...)` 句では非同期構造化例外がキャッチされません。 アクセス違反およびマネージド <xref:System.Exception?displayProperty=fullName> 例外がキャッチされず、非同期例外が処理される場合も含め、非同期例外が生成されたときに、スコープ内のオブジェクトが破棄されることはありません。

使用する場合 **/EHa**、イメージが大きい場合があり、コンパイラが最適化しないために、適切に機能しない実行可能性があります、**お試しください**ブロックを積極的にします。 また、コンパイラが C++ 例外をスローする可能性のあるコードを確認しない場合でも、すべてのローカル オブジェクトのデストラクターを自動的に呼び出す例外フィルターが除去されません。 これにより、非同期例外および C++ 例外のセーフ スタック アンワインドが可能になります。 使用すると **/EHs**、コンパイラは、例外できますでのみ発生することを想定しています、**スロー**ステートメントまたは関数呼び出し。 これにより、アンワインド可能オブジェクトの有効期間を管理するコードを削除できるため、コード サイズをかなり小さくできます。

使用してコンパイルされたオブジェクトをリンクしないことをお勧めします。 **/EHa**を使用してコンパイルされたオブジェクトと **/EHs**または **/EHsc**同じ実行可能モジュールでします。 モジュールの任意の場所で **/EHa** を使用して、非同期例外を処理する必要がある場合は、 **/EHa** を使用して、モジュール内のすべてのコードをコンパイルします。 構造化例外処理を使用してコンパイルされたコードと同じモジュールでの構文を使用する **/EHs**、SEH 構文とを混在させることはできませんが、**お試しください**、**スロー**、および**キャッチ**は同じ関数にします。

使用 **/EHa**以外の方法で発生した例外をキャッチするかどうか、**スロー**します。 この例では、構造化例外が生成され、キャッチされます。

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail() {   // generates SE and attempts to catch it using catch(...)
   try {
      int i = 0, j = 1;
      j /= i;   // This will throw a SE (divide by zero).
      printf("%d", j);
   }
   catch(...) {   // catch block will only be executed under /EHa
      cout<<"Caught an exception in catch(...)."<<endl;
   }
}

int main() {
   __try {
      fail();
   }

   // __except will only catch an exception here
   __except(EXCEPTION_EXECUTE_HANDLER) {
      // if the exception was not caught by the catch(...) inside fail()
      cout << "An exception was caught in __except." << endl;
   }
}
```

**/EHc** オプションでは、 **/EHs** または **/EHa** を指定する必要があります。 **/Clr**が暗黙的に指定 **/EHa** (つまり、 **/clr** **/EHa**が冗長です)。 コンパイラ エラーが発生 **/EHs**または **/EHsc**後で使用した **/clr**します。 最適化処理は、この動作に影響しません。 例外がキャッチされると、例外オブジェクトまたは例外と同じスコープ内にあるオブジェクトに対して、コンパイラが 1 つまたは複数のクラス デストラクターを呼び出します。 例外がキャッチされない場合は、これらのデストラクターは実行されません。

**/clr**に基づく例外処理の制約については、「 [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)」を参照してください。

マイナス記号 ( **-** ) を使用すると、このオプションをクリアできます。 たとえば、 **/EHsc-** として解釈される **/EHs** **/EHc-** と等価 **/EHs**します。

**/EHr**コンパイラ オプションを持つすべての関数でのランタイム終了チェックを有効にする**noexcept**属性。 既定では、コンパイラがバックエンドで関数が *スローしない* 関数のみを呼び出すと判断した場合に、ランタイム チェックが最適化され、除去されます。 スローしない関数とは、属性で例外がスローされないことが指定された関数を指します。 マークされた関数が含まれます**noexcept**、 `throw()`、`__declspec(nothrow)`と、 **/EHc**が指定されている**extern"C"** 関数。 スローしない関数には、コンパイラの検査でスローしないと判断された関数も含まれます。 **/EHr-** を使用して明示的に既定に設定することができます。

ただし、スローしない属性は、関数からどの例外もスローされないことを保証するわけではありません。 動作とは異なり、 **noexcept**関数、MSVC コンパイラは、使用して宣言された関数によってスローされる例外`throw()`、 `__declspec(nothrow)`、または**extern"C"** 未定義の動作として。 この 3 つの宣言属性を使用する関数は、例外のランタイム終了チェックを強制しません。 使用することができます、 **/EHr**エスケープする未処理の例外のランタイム チェックを生成するコンパイラを強制することで未定義の動作がこれを識別するためのオプション、 **noexcept**関数。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択**構成プロパティ** > **C/C++**  > **コード生成**します。

1. **[C++ の例外を有効にする]** プロパティを変更します。

   または、 **[C++ の例外を有効にする]** を **[いいえ]** に設定してから **[コマンド ライン]** プロパティ ページをクリックし、 **[追加のオプション]** ボックスにコンパイラ オプションを追加します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[エラーと例外処理](../../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[例外の仕様 (スロー)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[構造化例外処理 (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
