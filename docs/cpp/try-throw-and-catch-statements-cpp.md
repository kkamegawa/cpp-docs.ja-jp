---
title: try、throw、および catch ステートメント (C++)
ms.date: 11/04/2016
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
helpviewer_keywords:
- catch keyword [C++]
- keywords [C++], exception handling
- C++ exception handling, statement syntax
- try-catch keyword [C++], about try-catch exception handling
- throw keyword [C++]
- try-catch keyword [C++]
- try-catch keyword [C++], exception handling
- throwing exceptions [C++], throw keyword
- try-catch keyword [C++], throw keyword [C++]s
- throwing exceptions [C++], implementing C++ exception handling
- throwing exceptions [C++]
- throw keyword [C++], throw() vs. throw(...)
ms.assetid: 15e6a87b-b8a5-4032-a7ef-946c644ba12a
ms.openlocfilehash: 31ed5f7a17b9b45dbbecf5ccb29d2b51a7635eaa
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245143"
---
# <a name="try-throw-and-catch-statements-c"></a>try、throw、および catch ステートメント (C++)

でC++例外処理を実装するには、 **try**、 **throw**、および**catch**式を使用します。

最初に、try ブロックを使用し**て**、例外をスローする可能性のある1つ以上のステートメントを囲みます。

**Throw**式は、 **try**ブロックで例外的な条件 (多くの場合、エラー) が発生したことを通知します。 任意の型のオブジェクトを**throw**式のオペランドとして使用できます。 通常、このオブジェクトを使用してエラーに関する情報を通知します。 ほとんどの場合、 [std:: exception](../standard-library/exception-class.md)クラス、または標準ライブラリで定義されている派生クラスの1つを使用することをお勧めします。 これらのいずれのクラスも適さない場合は、`std::exception` から派生させた独自の例外クラスを使用することをお勧めします。

スローされる可能性のある例外を処理するには、 **try**ブロックの直後に1つ以上の**catch**ブロックを実装します。 各**catch**ブロックは、処理できる例外の種類を指定します。

この例では、 **try**ブロックとそのハンドラーを示します。 `GetNetworkResource()` では、ネットワーク接続を介してデータを取得するとします。また、2 つの型の例外として `std::exception` から派生させたユーザー定義のクラスを使用するとします。 **Catch**ステートメントで**const**参照によって例外がキャッチされていることに注意してください。 例外は値でスローし、const 参照でキャッチすることをお勧めします。

## <a name="example"></a>例

```cpp
MyData md;
try {
   // Code that could throw an exception
   md = GetNetworkResource();
}
catch (const networkIOException& e) {
   // Code that executes when an exception of type
   // networkIOException is thrown in the try block
   // ...
   // Log error message in the exception object
   cerr << e.what();
}
catch (const myDataFormatException& e) {
   // Code that handles another exception type
   // ...
   cerr << e.what();
}

// The following syntax shows a throw expression
MyData GetNetworkResource()
{
   // ...
   if (IOSuccess == false)
      throw networkIOException("Unable to connect");
   // ...
   if (readError)
      throw myDataFormatException("Format error");
   // ...
}
```

## <a name="remarks"></a>コメント

**Try**句の後のコードは、コードの保護されたセクションです。 **Throw**式は、例外を*スロー*します。 **Catch**句の後のコードブロックは、例外ハンドラーです。 これは、 **throw**および**catch**式の型に互換性がある場合にスローされる例外を*キャッチ*するハンドラーです。 **Catch**ブロックでの型の一致を制御する規則の一覧については、「 [Catch ブロックの評価方法](../cpp/how-catch-blocks-are-evaluated-cpp.md)」を参照してください。 **Catch**ステートメントで型の代わりに省略記号 (...) が指定されている場合、 **catch**ブロックはすべての種類の例外を処理します。 [/Eha](../build/reference/eh-exception-handling-model.md)オプションを使用してコンパイルすると、C 構造化例外、システム生成、またはアプリケーションによって生成される非同期例外 (メモリ保護、0除算、浮動小数点違反など) が含まれることがあります。 **Catch**ブロックはプログラムの順序で処理され、一致する型が検出されるため、省略記号ハンドラーは、関連付けられ**ている try**ブロックの最後のハンドラーである必要があります。 `catch(...)` は慎重に使用してください。プログラムの実行が継続されるには、キャッチした特定の例外を処理する方法を catch ブロックに記述する必要があります。 `catch(...)` ブロックは通常、プログラムの実行を停止する前に、エラーを記録して特別なクリーンアップを実行するために使用します。

オペランドが指定されていない**throw**式は、現在処理中の例外を再スローします。 この方法は例外を再スローするときにお勧めします。元の例外のポリモーフィックな型情報が保持されるためです。 このような式**は、catch ハンドラーまた**は**catch**ハンドラーから呼び出された関数でのみ使用してください。 再スローされた例外オブジェクトはコピーではなく元の例外オブジェクトです。

```cpp
try {
   throw CSomeOtherException();
}
catch(...) {
   // Catch all exceptions - dangerous!!!
   // Respond (perhaps only partially) to the exception, then
   // re-throw to pass the exception to some other handler
   // ...
   throw;
}
```

## <a name="see-also"></a>参照

[例外C++とエラー処理に関する最新のベストプラクティス](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)<br/>
[未処理の C++ 例外](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)