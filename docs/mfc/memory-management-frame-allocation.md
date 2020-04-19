---
title: メモリ管理:フレーム割り当て
ms.date: 11/04/2016
helpviewer_keywords:
- memory leaks [MFC], frame allocation
- memory [MFC], detecting leaks
- memory [MFC], reclaiming
- memory allocation [MFC], frames
- frame variables [MFC], automatic deletion of
- scope [MFC], frame variables
- heap allocation [MFC], vs. frame allocation
- variables [MFC], frame variables
- memory leaks [MFC], detecting
- memory, releasing [MFC]
- stack frames [MFC]
- memory leaks [MFC], allocating objects on the frame
- detecting memory leaks [MFC]
- frame allocation [MFC]
- frame variables [MFC]
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
ms.openlocfilehash: 1acf2ce89e18dd64c166103b59b5eb7007214efd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352128"
---
# <a name="memory-management-frame-allocation"></a>メモリ管理:フレーム割り当て

割り当てのフレームに設定されている「スタック フレーム」から名前を取得する関数が呼び出された時に常にします。 スタック フレームは、一時的に保持する引数に定義されている任意の変数と関数は、関数に対してローカル メモリの領域です。 フレーム変数は、コンパイラがそれらの領域を自動的に割り当てるために、多くの場合、「自動」の変数と呼ばれます。

フレームの割り当ての 2 つの主な特性があります。 最初に、ローカル変数を定義するときに十分な領域が割り当てられます全体の変数を保持するためにスタック フレーム場合でも、大きな配列またはデータ構造です。 次に、スコープ外に出るときにフレーム変数が自動的に削除します。

[!code-cpp[NVC_MFC_Utilities#10](../mfc/codesnippet/cpp/memory-management-frame-allocation_1.cpp)]

ローカル関数の変数のスコープが変化は、入れ子になった中かっこを使用する場合は、フレーム変数のスコープが、関数が終了を関数より小さくなることがある場合に起こります。 フレーム変数の自動削除が非常に重要です。 単純なプリミティブ型の場合 (など**int**または**バイト**)、配列、またはデータ構造では、自動的に削除されるだけです、変数で使用されるメモリを解放します。 変数がスコープ外に、ためか、アクセスできません。 C++ オブジェクトを自動削除のプロセスは少し複雑になります。

オブジェクトは、フレーム変数として定義するとき、定義が発生した時点では、コンス トラクターが自動的に呼び出されます。 オブジェクトがスコープ外になる、オブジェクトのメモリが解放される前に、デストラクターが自動的に起動します。 この自動構築と破棄は、非常に便利なできますが、デストラクターでは特に、自動呼び出しを認識する必要があります。

フレーム上のオブジェクトの割り当ての主な利点は、それらが自動的に削除されたことです。 フレームに、オブジェクトを割り当てるときは、忘れられたオブジェクトがメモリ リークの原因について心配する必要はありません。 (詳細については、メモリ リークは、記事を参照してください[MFC でのメモリ リークの検出](/previous-versions/visualstudio/visual-studio-2010/c99kz476(v=vs.100))。)。フレーム割り当ての欠点は、そのスコープ外にフレーム変数を使用できないことです。 フレームの割り当てとヒープ割り当てを選択する際にもう 1 つの要素とは大きな構造体とオブジェクトの場合は、多くの場合、スタック領域は限られた多くの場合、記憶域スタックの代わりにヒープを使用する方が適切です。

## <a name="see-also"></a>関連項目

[メモリ管理](../mfc/memory-management.md)
