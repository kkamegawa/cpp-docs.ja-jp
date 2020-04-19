---
title: CObject コレクションの全オブジェクトの削除
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], deleting in collections
- objects in CObject collections, deleting
- CObject class [MFC], deleting in collection
- collection classes [MFC], deleting all objects
- CObject class collection
- objects in CObject collections
- collection classes [MFC], shared objects
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
ms.openlocfilehash: 95d4cec61b230df5a019655617a25b1dc309cde4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153504"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>CObject コレクションの全オブジェクトの削除

この記事では、(コレクション オブジェクト自体を削除する) ことがなく、コレクション内のすべてのオブジェクトを削除する方法について説明します。

コレクション内のすべてのオブジェクトを削除する`CObject`s (またはから派生したオブジェクトの`CObject`)、この記事で説明されているイテレーション手法の 1 つを使用する[すべてのメンバーのコレクションにアクセスする](../mfc/accessing-all-members-of-a-collection.md)内の各オブジェクトを削除するには有効にします。

> [!CAUTION]
>  コレクション内のオブジェクトを共有することができます。 つまり、コレクション、オブジェクトへのポインターを保持するが、プログラムの他の部分は、同じオブジェクトへのポインターにもあります。 オブジェクトを使用して、すべての部分が完了するまで共有されているオブジェクトを削除しないように注意する必要があります。

この記事では、オブジェクトを削除する方法を示します。

- [一覧](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [配列](#_core_to_delete_all_elements_in_an_array)

- [マップ](#_core_to_delete_all_elements_in_a_map)

#### <a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>  CObject へのポインターのリスト内のすべてのオブジェクトを削除するには

1. 使用`GetHeadPosition`と`GetNext`リストを反復処理します。

1. 使用して、**削除**のイテレーションで検出された各オブジェクトを削除する演算子。

1. 呼び出す、`RemoveAll`それらの要素に関連付けられているオブジェクトを削除した後、一覧からすべての要素を削除する関数。

次の例の一覧からすべてのオブジェクトを削除する方法を示しています。`CPerson`オブジェクト。 リスト内の各オブジェクトはへのポインター、`CPerson`最初に、ヒープに割り当てられたオブジェクト。

[!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

最後の関数呼び出し`RemoveAll`は、リストからすべての要素を削除します。 リストのメンバー関数。 メンバー関数は、 `RemoveAt` 1 つの要素を削除します。

要素のオブジェクトを削除して、要素自体を削除する違いに注意してください。 リストから要素を削除すると、単なるオブジェクトへのリストの参照を削除します。 オブジェクトは、メモリに引き続き存在します。 オブジェクトを削除して消滅するので、メモリが再利用します。 したがって、存在しなくなったオブジェクトにアクセスする一覧が掲載されるよう、要素のオブジェクトが削除された後すぐに要素を削除する重要なは。

#### <a name="_core_to_delete_all_elements_in_an_array"></a>  配列内のすべての要素を削除するには

1. 使用`GetSize`と整数のインデックス値、配列を反復処理します。

1. 使用して、**削除**のイテレーションで検出された各要素を削除する演算子。

1. 呼び出す、`RemoveAll`が削除された後、配列からすべての要素を削除する関数。

   配列のすべての要素を削除するためのコードは次のとおりです。

   [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

上記リストの例でを呼び出すことができますと`RemoveAll`配列内のすべての要素を削除するまたは`RemoveAt`個々 の要素を削除します。

#### <a name="_core_to_delete_all_elements_in_a_map"></a> Map 内のすべての要素を削除するには

1. 使用`GetStartPosition`と`GetNextAssoc`配列を反復処理します。

1. 使用して、**削除**のイテレーションで検出された、キーや各マップ要素の値を削除する演算子。

1. 呼び出す、`RemoveAll`が削除された後、マップからすべての要素を削除する関数。

   すべての要素を削除するためのコードを`CMap`コレクションは、次のようにします。 マップ内の各要素が文字列をキーとして、`CPerson`オブジェクト (から派生した`CObject`) 値として。

   [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

呼び出すことができます`RemoveAll`マップ内のすべての要素を削除するまたは`RemoveKey`指定のキーを持つ個々 の要素を削除します。

## <a name="see-also"></a>関連項目

[コレクションの全メンバーへのアクセス](../mfc/accessing-all-members-of-a-collection.md)
