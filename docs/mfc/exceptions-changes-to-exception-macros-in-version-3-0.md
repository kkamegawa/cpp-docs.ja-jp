---
title: 例外:バージョン 3.0 での例外処理マクロの変更
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: fb51ad91e001f0ed153bf4fdb5aa598ab5ba5042
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173279"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>例外:バージョン 3.0 での例外処理マクロの変更

これは、高度なトピックです。

Mfc バージョン 3.0 以降では、例外処理マクロが C++ 例外を使用する変更されました。 この記事では、これらの変更が、マクロを使用する既存のコードの動作に影響を与えるように指示します。

ここでは、次のトピックについて説明します。

- [例外の種類と、CATCH マクロ](#_core_exception_types_and_the_catch_macro)

- [例外の再スロー](#_core_re.2d.throwing_exceptions)

##  <a name="_core_exception_types_and_the_catch_macro"></a> 例外の種類と、CATCH マクロ

MFC の以前のバージョンで、**CATCH**マクロでは、MFC の実行時の型情報を使用例外の種類を確認するには例外の型が決定されます、つまり、キャッチ側でします。 C++ の例外を除き、ただし、例外の型は常にスロー サイトによって決まりますスローされる例外オブジェクトの型。 スローされたオブジェクトへのポインターの型がスローされたオブジェクトの種類を異なる場所まれなケースで互換性が失われます。

次の例は、MFC バージョン 3.0 と以前のバージョンの間には、この違いの結果を示しています。

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

このコードはバージョン 3.0 で異なる動作制御が常に最初に渡されるため、**catch**と一致する例外-宣言ブロックします。 スロー式の結果

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

としてスローされる、`CException*`として構築した場合でも、`CCustomException`します。 **CATCH**以前使用して MFC バージョン 2.5 マクロ`CObject::IsKindOf`実行時に、型をテストします。 式

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

true の場合、最初の catch ブロックが例外をキャッチします。 C++ 例外を使用して、例外処理マクロの多くを実装する、バージョン 3.0 では、2 番目の catch ブロックと一致する、スローされた`CException`します。

このようなコードは一般的ではありません。 例外オブジェクトがジェネリック型を受け取る別の関数に渡されるときに通常表示`CException*`「スロー」の処理を行い、最後に、例外をスローします。

この問題を回避するには、スロー式を関数から呼び出し元のコードに移動し、例外の生成時にコンパイラに判明する実際の型の例外をスローします。

##  <a name="_core_re.2d.throwing_exceptions"></a> 例外の再スロー

Catch ブロックでは、その例外はキャッチ例外ポインターと同じをスローできません。

たとえば、このコードは以前のバージョンで有効ですがバージョン 3.0 での予期しない結果。

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

使用して**THROW** catch ブロックが、ポインター`e`外側の catch のサイトは無効なポインターを受け取れるように、削除します。 使用**THROW_LAST**再スローする`e`します。

詳細については、次を参照してください。[例外:キャッチと削除例外](../mfc/exceptions-catching-and-deleting-exceptions.md)します。

## <a name="see-also"></a>関連項目

[例外処理](../mfc/exception-handling-in-mfc.md)
