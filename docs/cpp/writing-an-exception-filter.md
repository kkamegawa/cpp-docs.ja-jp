---
title: 例外フィルターの記述
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: aaf0dc77207399d7c6be86127d7decf03895ced5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245987"
---
# <a name="writing-an-exception-filter"></a>例外フィルターの記述

例外は、例外ハンドラーのレベルにジャンプするか、実行を続けるかのいずれかにより、処理できます。 例外ハンドラーコードを使用して例外を処理し、遅延を解消する代わりに、*フィルター*を使用して問題をクリーンアップし、-1 を返すことで、スタックをクリアせずに通常のフローを再開できます。

> [!NOTE]
>  一部の例外は、続行できない場合があります。 このような例外に対して*filter*が-1 と評価された場合、システムによって新しい例外が発生します。 [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception)を呼び出すと、例外を続行するかどうかが決定されます。

たとえば、次のコードでは、*フィルター*式で関数呼び出しを使用しています。この関数は問題を処理し、-1 を返して通常の制御フローを再開します。

```cpp
// exceptions_Writing_an_Exception_Filter.cpp
#include <windows.h>
int main() {
   int Eval_Exception( int );

   __try {}

   __except ( Eval_Exception( GetExceptionCode( ))) {
      ;
   }

}
void ResetVars( int ) {}
int Eval_Exception ( int n_except ) {
   if ( n_except != STATUS_INTEGER_OVERFLOW &&
      n_except != STATUS_FLOAT_OVERFLOW )   // Pass on most exceptions
   return EXCEPTION_CONTINUE_SEARCH;

   // Execute some code to clean up problem
   ResetVars( 0 );   // initializes data to 0
   return EXCEPTION_CONTINUE_EXECUTION;
}
```

フィルターで複雑な処理を*行う必要が*ある場合は常に、*フィルター*式で関数呼び出しを使用することをお勧めします。 式を評価すると、関数 (この場合、`Eval_Exception`) が実行されます。

[Getexceptioncode](/windows/win32/Debug/getexceptioncode)を使用して例外を特定することに注意してください。 この関数は、フィルター自体の内部で呼び出す必要があります。 `Eval_Exception` は `GetExceptionCode`を呼び出すことはできませんが、例外コードを渡す必要があります。

このハンドラーは、例外が整数または浮動小数点数のオーバーフローでなければ、他のハンドラーに制御を渡します。 オーバーフローがあった場合、ハンドラーは関数 (`ResetVars` は一例で、API 関数ではありません) を呼び出して、いくつかのグローバル関数をリセットします。 この例では空である*ステートメントブロック 2*は、`Eval_Exception` が EXCEPTION_EXECUTE_HANDLER (1) を返さないため、実行できません。

関数呼び出しの使用は、複雑なフィルター式を処理するための優れた汎用的手法です。 その他の便利な 2 つの C 言語機能を次に示します。

- 条件演算子

- コンマ演算子

条件演算子を使用すると、特定のリターン コードをチェックしてから 2 つの異なる値のいずれかを返すことができるため、この演算子は多くの場合に役立ちます。 たとえば、次のコードのフィルターでは、例外が STATUS_INTEGER_OVERFLOW 場合にのみ例外が認識されます。

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

次のコードでは同じ結果が生成されるため、ここでは条件演算子が主として明確さを高めるために使用されています。

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

条件演算子は、フィルターを-1、EXCEPTION_CONTINUE_EXECUTION に評価する必要がある場合に便利です。

コンマ演算子を使用すると、1 つの式内で複数の個別演算を実行できます。 複数のステートメントを実行してから最後の式の値を返す場合とほぼ同じ効果が得られます。 たとえば、次のコードでは、変数に例外コードを保存してから、そのコードをテストしています。

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>参照

[例外ハンドラーの記述](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)