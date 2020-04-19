---
title: MSVC での例外処理
ms.date: 11/19/2019
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 6cf71d6e6d0519951a084ebead65003bd363395f
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246589"
---
# <a name="exception-handling-in-msvc"></a>MSVC での例外処理

例外とは、プログラムが通常の実行パスに沿って進むことを妨げるエラー状態のことであり、プログラムで制御できない可能性があります。 オブジェクトの作成、ファイルの入出力、および他のモジュールから行われる関数呼び出しを含む特定のアクションは、プログラムが正しく実行されている場合でも、すべて例外の潜在的な原因となります。 堅牢なコードは例外を予期し、それを処理します。 ロジックエラーを検出するには、例外ではなくアサーションを使用します (「 [Using assertion」を](/visualstudio/debugger/c-cpp-assertions)参照してください)。

## <a name="kinds-of-exceptions"></a>例外の種類

Microsoft C++コンパイラ (MSVC) では、次の3種類の例外処理がサポートされています。

- [C++例外処理](errors-and-exception-handling-modern-cpp.md)

   ほとんどの C++ プログラムでは、タイプ セーフでオブジェクトのデストラクターがスタック アンワインド中に確実に呼び出されるようにする、C++ 例外処理を使用する必要があります。

- [構造化例外処理](structured-exception-handling-c-cpp.md)

   Windows には、SEH と呼ばれる独自の例外機構が備わっています。 これは C++ または MFC プログラミングには推奨されません。 SEH は、非 MFC C プログラムでのみ使用してください。

- [MFC の例外](../mfc/exception-handling-in-mfc.md)

プロジェクトで使用する例外処理の種類を指定するには、 [/EH](../build/reference/eh-exception-handling-model.md)コンパイラオプションを使用します。C++例外処理が既定値です。 エラー処理機構を併用しないでください。たとえば、構造化例外処理で C++ 例外を使用しないでください。 C++ 例外処理を使用すると、コードの移植性が高くなり、すべての種類の例外を処理できるようになります。 構造化例外処理の欠点の詳細については、「[構造化例外処理](structured-exception-handling-c-cpp.md)」を参照してください。 MFC マクロとC++例外の混在に関するアドバイスについては、「[例外C++ : Mfc マクロと例外の使用](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)」を参照してください。

## <a name="in-this-section"></a>このセクションの内容

- [例外C++とエラー処理に関する最新のベストプラクティス](errors-and-exception-handling-modern-cpp.md)

- [例外の安全性を確保するための設計方法](how-to-design-for-exception-safety.md)

- [例外的なコードと非例外的なコードの間をインターフェイスする方法](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [Try、catch、および throw ステートメント](try-throw-and-catch-statements-cpp.md)

- [catch ブロックの評価方法](how-catch-blocks-are-evaluated-cpp.md)

- [例外とスタックアンワインド](exceptions-and-stack-unwinding-in-cpp.md)

- [例外の指定](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [未処理の C++ 例外](unhandled-cpp-exceptions.md)

- [C (構造化) と C++ の混合例外](mixing-c-structured-and-cpp-exceptions.md)

- [構造化例外処理 (SEH) (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>参照

[C++ 言語リファレンス](cpp-language-reference.md)</br>
[x64 の例外処理](../build/exception-handling-x64.md)</br>
[例外処理 (C++/Cli およびC++/cx)](../extensions/exception-handling-cpp-component-extensions.md)
