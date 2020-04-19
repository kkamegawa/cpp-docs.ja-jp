---
title: スタック コレクションとキュー コレクションの作成
ms.date: 11/04/2016
helpviewer_keywords:
- MFC collection classes [MFC], stack collections
- collections, stack
- stack
- collection classes [MFC], creating
- queue collections
- MFC collection classes [MFC], queue collections
- stack collections
- collections, queue
ms.assetid: 3c7bc198-35f0-4fc3-aaed-6005a0f22638
ms.openlocfilehash: ed0ad9b98a69e56df4e66b25bc6ca08cdaaad413
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242407"
---
# <a name="creating-stack-and-queue-collections"></a>スタック コレクションとキュー コレクションの作成

この記事は、他のデータ構造を作成する方法を説明します[スタック](#_core_stacks)と[キュー](#_core_queues)、MFC クラスのリストします。 派生したクラスを使用して、例では、 `CList`、使用することができますが、`CList`直接機能を追加する必要がある場合を除き、します。

##  <a name="_core_stacks"></a> スタック

標準のリスト コレクションには、先頭と末尾の両方があるために、後入れ先出しスタックの動作を模倣した派生リスト コレクションの作成が容易になります。 スタックでは、カフェテリアにトレイのスタックのようにします。 トレイがスタックに追加される、スタックの一番上が移動します。 追加された最後のトレイは、最初に削除します。 リスト コレクションのメンバー関数は、`AddHead`と`RemoveHead`を追加する使用できます。 具体的には、リストの先頭から要素を削除し、はそのため、最も最近追加された要素が最初に削除します。

#### <a name="to-create-a-stack-collection"></a>スタック コレクションを作成するには

1. 既存の MFC のリストのクラスのいずれかから新しいリスト クラスを派生し、スタック操作の機能をサポートするメンバー関数を追加します。

   次の例では、スタック、スタックの最上位の要素でピークに要素をプッシュして、スタックからの最上位の要素をポップするメンバー関数を追加する方法を示します。

   [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_1.h)]

このアプローチは、基になる公開注`CObList`クラス。 ユーザーは、いずれかを呼び出すことができます`CObList`メンバー関数は、合理的スタックのかどうかどうか。

##  <a name="_core_queues"></a> キュー

標準のリスト コレクションには、先頭と末尾の両方があるためにも最初先出しキューの動作を模倣した派生リスト コレクションを作成する簡単です。 キューでは、カフェテリアに人のようにします。 行の最初の人を提供します。 多くの人が、順番を待機する行の末尾に移動します。 リスト コレクションのメンバー関数は、`AddTail`と`RemoveHead`を追加する使用できます。 具体的には、head またはリストの末尾から要素を削除とはそのため、最も最近追加された要素は、常に最後に削除されます。

#### <a name="to-create-a-queue-collection"></a>キューのコレクションを作成するには

1. Microsoft Foundation Class ライブラリで提供される定義済みリストのクラスのいずれかから新しいリスト クラスを派生し、キュー操作のセマンティクスをサポートするメンバー関数を追加します。

   次の例では、キューの末尾に要素を追加し、キューの先頭から要素を取得するメンバー関数を追加する方法を示します。

   [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/cpp/creating-stack-and-queue-collections_2.h)]

## <a name="see-also"></a>関連項目

[コレクション](../mfc/collections.md)
