---
title: try-except ステートメント
ms.date: 10/09/2018
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- EXCEPTION_CONTINUE_SEARCH
- _exception_info
- __except
- _except
- EXCEPTION_CONTINUE_EXECUTION
- _exception_code
- __except_cpp
- _exception_info_cpp
- EXCEPTION_EXECUTE_HANDLER
- _abnormal_termination
helpviewer_keywords:
- __try keyword [C++]
- EXCEPTION_CONTINUE_EXECUTION macro
- EXCEPTION_CONTINUE_SEARCH macro
- EXCEPTION_EXECUTE_HANDLER macro
- GetExceptionCode function
- try-catch keyword [C++], try-except keyword [C++]
- _exception_code keyword [C++]
- try-except keyword [C++]
- _exception_info keyword [C++]
- _abnormal_termination keyword [C++]
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
ms.openlocfilehash: af378f510f11e1fe7d08619b5f33efe92a13d7be
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245169"
---
# <a name="try-except-statement"></a>try-except ステートメント

**Microsoft 固有の仕様**

**Try-except**ステートメントは、構造化例外処理をサポートする C C++言語および言語の Microsoft 拡張機能です。

## <a name="syntax"></a>構文

> **\_\_試してみる**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;//保護されたコード<br/>
> }<br/>
> **except\_\_** (*式*)<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;//例外ハンドラーコード<br/>
> }

## <a name="remarks"></a>コメント

**Try-except**ステートメントは、C とC++言語の Microsoft 拡張機能であり、通常、プログラムの実行を終了するイベントが発生したときに対象アプリケーションが制御できるようにします。 このようなイベントは*例外*と呼ばれ、例外を処理する機構は*構造化例外処理*(SEH) と呼ばれます。

関連情報については、「 [try finally ステートメント](../cpp/try-finally-statement.md)」を参照してください。

例外は、ハードウェア例外またはソフトウェア例外です。 アプリケーションがハードウェア例外またはソフトウェア例外から完全に回復できない場合でも、構造化例外処理はエラー情報を表示し、問題の診断に役立つアプリケーションの内部状態をトラップすることができます。 これは、簡単に再現できない断続的な問題の場合に特に便利です。

> [!NOTE]
> 構造化例外処理では、C と C++ のソース ファイルの両方で Win32 を使用します。 ただし、特に C++ 用にデザインされたものではありません。 C++ 例外処理を使用して、コードの移植性を高めることができます。 また、C++ 例外処理は、任意の型の例外を処理できるという点で、より柔軟です。 プログラムC++については、 C++例外処理機構 ([try、catch、および throw](../cpp/try-throw-and-catch-statements-cpp.md)ステートメント) を使用することをお勧めします。

**__Try**句の後の複合ステートメントは、本体または保護されたセクションです。 **__Except**句の後の複合ステートメントは、例外ハンドラーです。 ハンドラーは、保護されたセクションの本体の実行中に例外が発生した場合に行われる一連の操作を指定します。 次のように実行されます。

1. 保護されたセクションが実行されます。

1. 保護されたセクションの実行中に例外が発生しなかった場合は、 **__except**句の後のステートメントから実行が続行されます。

1. 保護されたセクションの実行中、または保護されたセクションがを呼び出すルーチンで例外が発生した場合、 **__except** *式*(*フィルター*式) が評価され、値によって例外の処理方法が決まります。 指定できる値は 3 つあります。

   - EXCEPTION_CONTINUE_EXECUTION (-1) 例外は破棄されます。 例外が発生した位置から実行を継続します。

   - EXCEPTION_CONTINUE_SEARCH (0) 例外は認識されません。 最初に **try-except** ステートメントを含むハンドラーを検索してから、次に優先順位が最も高いハンドラーについてスタックを検索し続けます。

   - EXCEPTION_EXECUTE_HANDLER (1) 例外が認識されています。 **__Except**複合ステートメントを実行して例外ハンドラーに制御を移し、 **__except**ブロックの後に実行を継続します。

**__Except**式は C の式として評価されるため、1つの値、条件式の演算子、またはコンマ演算子に制限されます。 より広範な処理が必要な場合、前に挙げた 3 つの値の 1 つを返すルーチンを式で呼び出すことができます。

各アプリケーションが独自の例外ハンドラーを持つ場合があります。

**__Try**ステートメントにジャンプすることはできませんが、1つのステートメントからジャンプすることは有効です。 **Try-except**ステートメントの実行中にプロセスが終了した場合、例外ハンドラーは呼び出されません。

以前のバージョンとの互換性を維持するために、 **_try**、 **_except**、および **_leave**は、コンパイラオプション[/Za __except 言語拡張を無効にする)](../build/reference/za-ze-disable-language-extensions.md)が指定されていない限り、 **__try**、 **__leave**、および **\(** のシノニムです。

### <a name="the-__leave-keyword"></a>__leave キーワード

**__Leave**キーワードは、 **try-except**ステートメントの保護されたセクション内でのみ有効であり、その結果、保護されたセクションの末尾に移動します。 実行は、例外ハンドラーの後の最初のステートメントから続行されます。

**Goto**ステートメントは、保護されたセクションからジャンプすることもできます。また、スタックアンワインドが発生しないため、 **try-catch**ステートメントの場合と同様にパフォーマンスが低下することはありません。 ただし、 **goto**ステートメントではなく、 **__leave**キーワードを使用することをお勧めします。これは、保護されたセクションが大規模または複雑な場合にプログラミングの間違いを犯す可能性が低いためです。

### <a name="structured-exception-handling-intrinsic-functions"></a>構造化例外処理の組み込み関数

構造化例外処理には、 **try-except**ステートメントで使用できる2つの組み込み関数が用意されています。 `GetExceptionCode` と `GetExceptionInformation`です。

`GetExceptionCode` は、例外のコード (32 ビット整数) を返します。

組み込み関数 `GetExceptionInformation` は、例外に関する追加情報を含む構造体へのポインターを返します。 このポインターを使用して、ハードウェア例外のときに存在していたコンピューターの状態にアクセスできます。 その構造は次のとおりです。

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

`PEXCEPTION_RECORD` と `PCONTEXT` のポインター型はインクルードファイル \<winnt.h > に定義されており、`_EXCEPTION_RECORD` と `_CONTEXT` はインクルードファイル \<excpt.h に定義されてい >

例外ハンドラー内で `GetExceptionCode` を使用できます。 ただし、`GetExceptionInformation` は、例外フィルター式内でのみ使用できます。 これが示す情報は、一般的にスタックにあり、制御が例外ハンドラーに移されると使用できなくなります。

組み込み関数 `AbnormalTermination` は、終了ハンドラー内で使用できます。 **Try finally**ステートメントの本体が連続して終了する場合は、0を返します。 その他の場合は、1 を返します。

excpt.h は、これらの組み込みの代替名を定義します。

`GetExceptionCode` は `_exception_code` と同じです。

`GetExceptionInformation` は `_exception_info` と同じです。

`AbnormalTermination` は `_abnormal_termination` と同じです。

## <a name="example"></a>例

```cpp
// exceptions_try_except_Statement.cpp
// Example of try-except and try-finally statements
#include <stdio.h>
#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION
#include <excpt.h>

int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep)
{
    puts("in filter.");
    if (code == EXCEPTION_ACCESS_VIOLATION)
    {
        puts("caught AV as expected.");
        return EXCEPTION_EXECUTE_HANDLER;
    }
    else
    {
        puts("didn't catch AV, unexpected.");
        return EXCEPTION_CONTINUE_SEARCH;
    };
}

int main()
{
    int* p = 0x00000000;   // pointer to NULL
    puts("hello");
    __try
    {
        puts("in try");
        __try
        {
            puts("in try");
            *p = 13;    // causes an access violation exception;
        }
        __finally
        {
            puts("in finally. termination: ");
            puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");
        }
    }
    __except(filter(GetExceptionCode(), GetExceptionInformation()))
    {
        puts("in except");
    }
    puts("world");
}
```

### <a name="output"></a>出力

```Output
hello
in try
in try
in filter.
caught AV as expected.
in finally. termination:
        abnormal
in except
world
```

**END Microsoft 固有の仕様**

## <a name="see-also"></a>参照

[例外ハンドラーの記述](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)
