---
title: '例外処理のタイミング: 概要'
ms.date: 05/07/2019
helpviewer_keywords:
- sequence [C++]
- sequence, of handlers
- exception handling [C++], timing
- setjmpex.h
- termination handlers [C++], timing
- setjmp.h
- handlers [C++], order of exception
- structured exception handling [C++], timing
ms.assetid: 5d1da546-73fd-4673-aa1a-7ac0f776c420
ms.openlocfilehash: 870606c3661df3654581760214e48ef2bdfb1987
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246330"
---
# <a name="timing-of-exception-handling-a-summary"></a>例外処理のタイミング: 概要

**__Try**ステートメントブロックの終了方法に関係なく、終了ハンドラーが実行されます。 **__Try**ブロックからのジャンプ、ブロックの外部で制御を転送する `longjmp` ステートメント、例外処理によるスタックのアンワインドなどが発生します。

> [!NOTE]
>  Microsoft C++コンパイラでは、2つの形式の `setjmp` と `longjmp` ステートメントがサポートされています。 高速なバージョンは終了処理をバイパスしますが、より効率的です。 このバージョンを使用するには、ファイル \<setjmp. h > を含めます。 もう一方のバージョンは、前の段落で説明したような終了処理をサポートします。 このバージョンを使用するには、ファイル \<setjmpex.h > を含めます。 高速バージョンでパフォーマンスがどの程度向上するかは、ハードウェア構成によって異なります。

オペレーティング システムは、例外ハンドラー本体を含む他のあらゆるコードを実行する前に、適切な順序ですべての終了ハンドラーを実行します。

中断の原因が例外の場合、システムは終了対象を決める前に、最初に 1 つ以上の例外ハンドラーのフィルター部分を実行する必要があります。 イベントの順序は次のとおりです。

1. 例外が発生します。

1. システムは、アクティブな例外ハンドラーの階層を参照し、最も優先順位が高いハンドラーのフィルターを実行します。これは、ブロックと関数呼び出しの点から見て、最も後にインストールされ、最も深く入れ子になった例外ハンドラーです。

1. 制御がこのフィルターを通過する (フィルターが 0 を返す) と、制御が通過できないフィルターが見つかるまで処理が続行されます。

1. このフィルターが-1 を返した場合、例外が発生した場所で実行が続行され、終了は行われません。

1. フィルターが 1 を返すと、次のイベントが発生します。

   - システムは、スタックをアンワインドし、現在実行中のコード (例外が発生した場所) と制御を取得している例外ハンドラーを含むスタック フレームの間のすべてのスタック フレームをクリアします。

   - スタックがアンワインドされると、スタックの各終了ハンドラーが実行されます。

   - 例外ハンドラー自体が実行されます。

   - この例外ハンドラーの末尾の後ろのコード行に制御が進みます。

## <a name="see-also"></a>参照

[終了ハンドラーの記述](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
