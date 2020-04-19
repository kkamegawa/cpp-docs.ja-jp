---
title: C (構造化) と例外C++の混合
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: e49731f1c81057002eaae2bef16cda4a5cf86f8d
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246461"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>C (構造化) と例外C++の混合

移植可能なコードを記述する場合は、 C++プログラムで構造化例外処理 (SEH) を使用することは推奨されません。 ただし、 [/eha](../build/reference/eh-exception-handling-model.md)を使用してコンパイルし、構造化例外とC++ソースコードを混在させ、両方の種類の例外を処理するための機能が必要になる場合があります。 構造化例外ハンドラーには、オブジェクトまたは型指定された例外の概念がないためC++ 、コードによってスローされた例外を処理することはできません。 ただし、C++**catch**ハンドラーは、構造化例外を処理できます。 C++例外処理構文 (**try**、**throw**、**catch**) が、C コンパイラは構造化例外処理の構文で受け入れられない ( **__try**、 **__except**、 **__finally**) でサポートされて、C++コンパイラ。

構造化例外を例外としてC++処理する方法については、「[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)」を参照してください。

構造化された例外C++と例外を混在させる場合は、次の潜在的な問題に注意してください。

- C++ の例外と構造化例外を、同じ関数内で混在させることはできません。

- 終了ハンドラー ( **__finally**ブロック)、例外がスローされた後のアンワインド中にも、常に実行します。

- C++例外処理では、 [/EH](../build/reference/eh-exception-handling-model.md)コンパイラオプションを使用してコンパイルされたすべてのモジュールでアンワインドセマンティクスをキャッチおよび保持できます。これにより、アンワインドセマンティクスが可能になります

- デストラクター関数がすべてのオブジェクトに対して呼び出されない状況もあります。 たとえば、初期化されていない関数ポインターを使用して関数呼び出しを行うときに構造化例外が発生し、その関数が呼び出し前に構築されたパラメーターオブジェクトとしてを受け取る場合、それらのオブジェクトのデストラクターは呼び出されません。スタックのアンワインド中。

## <a name="next-steps"></a>次の手順

- [プログラムでC++ setjmp または longjmp を使用する](../cpp/using-setjmp-longjmp.md)

  `setjmp` と `longjmp` の使用方法の詳細についてC++は、「プログラム」を参照してください。

- [C++ での構造化例外の処理](../cpp/exception-handling-differences.md)

  構造化例外の処理に使用C++できる方法の例を参照してください。

## <a name="see-also"></a>関連項目

[例外C++とエラー処理に関する最新のベストプラクティス](../cpp/errors-and-exception-handling-modern-cpp.md)
