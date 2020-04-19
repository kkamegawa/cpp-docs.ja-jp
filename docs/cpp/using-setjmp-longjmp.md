---
title: Setjmp と longjmp の使用
ms.date: 08/14/2018
f1_keywords:
- longjmp_cpp
- setjmp_cpp
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
ms.openlocfilehash: 4ead12f79701899b3977993c9de3c3803023150f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364520"
---
# <a name="using-setjmp-and-longjmp"></a>Setjmp と longjmp の使用

ときに[setjmp](../c-runtime-library/reference/setjmp.md)と[longjmp](../c-runtime-library/reference/longjmp.md)は非ローカルを実行する方法を提供を一緒に使用**goto**します。 これらは、標準呼び出しを使用せず、以前に呼び出されたルーチンのエラー処理または回復コードに実行制御を渡す C コードで通常使用される規約や復帰規約。

> [!CAUTION]
> `setjmp`と`longjmp`C++ コンパイラ、間で移植のスタック フレーム オブジェクトの適切な破棄をサポートしていないし、C++ での使用をお勧めしませんので、ローカル変数の最適化を防ぐことによって、パフォーマンスが低下する可能性があります、プログラム。 使用することをお勧めします。**try**と**catch**代わりに構築します。

使用する場合`setjmp`と`longjmp`、C++ プログラムでも含める\<setjmp.h > または\<setjmpex.h > 関数と構造化例外処理 (SEH) または C++ の例外の間の相互作用処理します。

**Microsoft 固有の仕様**

使用する場合、 [/EH](../build/reference/eh-exception-handling-model.md) C++ コードをコンパイルするオプションで、ローカル オブジェクトのデストラクターがスタック アンワインド中に呼び出されます。 ただし、使用する場合 **/EHs**または **/EHsc**コンパイル、および使用する関数の 1 つに[noexcept](../cpp/noexcept-cpp.md)呼び出し`longjmp`デストラクターは、その関数をアンワインドし、発生しない場合、オプティマイザーの状態に応じて。

移植可能なコードは、のときに、`longjmp`呼び出しが実行フレーム ベースのオブジェクトの適切な破棄は、標準で明示的にはことが保証され、他のコンパイラでサポートされていない可能性があります。 警告レベル 4 への呼び出しを通知する`setjmp`警告 C4611: '_setjmp' 間の相互作用とC++オブジェクトの破棄はポータブルでないです。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[C (構造化) と C++ の混合例外](../cpp/mixing-c-structured-and-cpp-exceptions.md)
