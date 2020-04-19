---
title: テンプレート ベースのクラス
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections
- CTypedPtrList class [MFC], template-based classes
- arrays [MFC], classes
- arrays [MFC], pointers
- typed pointers, collections of
- arrays [MFC], template-based
- CArray class [MFC], template-based classes
- simple template-based collections
- simple array collection classes [MFC]
- typed pointers
- collections, typed-pointer
- CList class [MFC], template-based classes
- collection classes [MFC], template-based
- CTypedPtrMap class [MFC], template-based classes
- pointers, collections of typed
- CTypedPtrArray class [MFC], template-based classes
- MFC collection classes [MFC], template-based
- template-based collection classes [MFC]
- simple list collection classes [MFC]
ms.assetid: c69fc95b-c8f6-4a99-abed-517c9898ef0c
ms.openlocfilehash: 40633c8b2b09d27e97443364ed3ce711ee217e18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306393"
---
# <a name="template-based-classes"></a>テンプレート ベースのクラス

この記事では、MFC バージョン 3.0 以降では、タイプ セーフ テンプレート ベースのコレクション クラスについて説明します。 方が便利ではこれらのテンプレートを使用して、タイプ セーフなコレクションを作成して、タイプ セーフをテンプレートに基づいていないコレクション クラスを使用するよりもより効果的に実現します。

MFC 事前テンプレート ベースのコレクションの 2 つのカテゴリに定義します。

- [単純な配列、リスト、およびマップ クラス](#_core_using_simple_array.2c_.list.2c_.and_map_templates)

   `CArray`、 `CList`、 `CMap`

- [配列、リスト、および型指定されたポインターのマップ](#_core_using_typed.2d.pointer_collection_templates)

   `CTypedPtrArray`、 `CTypedPtrList`、 `CTypedPtrMap`

単純なコレクション クラスのすべてのクラスから派生`CObject`シリアル化、動的な作成は、その他のプロパティが継承されるよう、`CObject`します。 型付きポインター コレクション クラスから派生するクラスを指定する必要があります: などの MFC で定義済みテンプレート ポインター コレクションのいずれかを指定する必要があります`CPtrList`または`CPtrArray`します。 指定した基本クラスから新しいコレクション クラスを継承し、新しいクラスのメンバー関数では、基本クラスのメンバーをカプセル化された呼び出しを使用して、タイプ セーフを適用します。

C++ テンプレートの詳細については、次を参照してください。[テンプレート](../cpp/templates-cpp.md)で、 *C++ 言語リファレンス*します。

##  <a name="_core_using_simple_array.2c_.list.2c_.and_map_templates"></a> 単純な配列、リスト、およびマップ テンプレートを使用します。

単純なコレクションのテンプレートを使用するには、これらのコレクションに格納できるデータの種類と、コレクションを宣言で使用するには、どのようなパラメーターを把握する必要があります。

###  <a name="_core_simple_array_and_list_usage"></a> 単純な配列とリストの使用状況

単純な配列とリストのクラス、 [CArray](../mfc/reference/carray-class.md)と[CList](../mfc/reference/clist-class.md)、2 つのパラメーターします。*型*と`ARG_TYPE`します。 これらのクラスで指定した任意のデータ型を格納できる、*型*パラメーター。

- などの基本的な C++ のデータ型**int**、 **char**、および**float**

- C++ 構造体とクラス

- 定義したその他の型

利便性と効率性は、使用することができます、*中*関数の引数の型を指定するパラメーター。 通常を指定する*中*でという名前の型への参照として、*型*パラメーター。 例:

[!code-cpp[NVC_MFCCollections#1](../mfc/codesnippet/cpp/template-based-classes_1.cpp)]

最初の例は、配列のコレクションを宣言します`myArray`を格納している**int**秒。 2 番目の例では、宣言のリスト コレクション、 `myList`、格納する`CPerson`オブジェクト。 コレクション クラスのメンバー関数は、によって指定された型の引数を受け取る、*中*テンプレート パラメーター。 たとえば、`Add`クラスのメンバー関数`CArray`は、*中*引数。

[!code-cpp[NVC_MFCCollections#2](../mfc/codesnippet/cpp/template-based-classes_2.cpp)]

###  <a name="_core_simple_map_usage"></a> 単純なマップの使用

単純なマップ クラス[CMap](../mfc/reference/cmap-class.md)、4 つのパラメーターします。*キー*、 *ARG_KEY*、*値*、および*ARG_VALUE*します。 配列とリストのクラスと同様、マップ クラスは、任意のデータ型を格納できます。 マップは、配列と、インデックスを付け、保存データの並べ替え、リストとは異なり、キーと値を関連付けます。値の関連付けられているキーを指定することで、マップに格納されている値にアクセスします。 *キー*パラメーターがマップに格納されているデータへのアクセスに使用されるキーのデータ型を指定します。 場合の種類*キー*構造体またはクラスでは、 *ARG_KEY*パラメーターがで指定された型への参照では通常*キー*します。 *値*パラメーターがマップに格納されている項目の種類を指定します。 場合の種類*ARG_VALUE*構造体またはクラスでは、 *ARG_VALUE*パラメーターがで指定された型への参照では通常*値*します。 例:

[!code-cpp[NVC_MFCCollections#3](../mfc/codesnippet/cpp/template-based-classes_3.cpp)]

最初の例のストア`MY_STRUCT`値にアクセスして**int**キー、およびアクセス返します`MY_STRUCT`参照によって項目。 2 番目の例のストア`CPerson`値にアクセスして`CString`キー、およびアクセスした項目への参照を返します。 この例を検索する人物をして、姓、単純なアドレス帳を表すことができます。

*キー*型のパラメーターが`CString`と*KEY_TYPE*型のパラメーターが`LPCSTR`、アイテムの種類として、マップ内のキーが格納されている`CString`内で参照されますが、などの関数`SetAt`型のポインターによって`LPCSTR`します。 例:

[!code-cpp[NVC_MFCCollections#4](../mfc/codesnippet/cpp/template-based-classes_4.cpp)]

##  <a name="_core_using_typed.2d.pointer_collection_templates"></a> 型付きポインター コレクションのテンプレートを使用します。

型付きポインター コレクション テンプレートを使用するには、これらのコレクションに格納できるデータの種類と、コレクションを宣言で使用するには、どのようなパラメーターを把握する必要があります。

###  <a name="_core_typed.2d.pointer_array_and_list_usage"></a> 型指定されたポインターの配列とリストの使用状況

型指定されたポインターの配列とリストのクラス、 [CTypedPtrArray](../mfc/reference/ctypedptrarray-class.md)と[CTypedPtrList](../mfc/reference/ctypedptrlist-class.md)、2 つのパラメーターします。*BASE_CLASS*と*型*します。 これらのクラスで指定した任意のデータ型を格納できる、*型*パラメーター。 ポインターを格納する非テンプレート コレクション クラスのいずれかから派生しています。この基本クラスを指定する*BASE_CLASS*します。 配列のいずれかを使用して`CObArray`または`CPtrArray`します。 一覧については、いずれかの操作を使用して`CObList`または`CPtrList`します。

実際には、に基づいてコレクションを宣言するときに答えて`CObList`、新しいクラスだけでなく、その基底クラスのメンバーを継承が、追加のタイプ セーフなメンバー関数とカプセル化することによってタイプ セーフが提供される演算子も宣言基本クラスのメンバーの呼び出し。 これらをカプセル化では、すべての必要な型変換を管理します。 例:

[!code-cpp[NVC_MFCCollections#5](../mfc/codesnippet/cpp/template-based-classes_5.cpp)]

最初の例では、型付きポインターの配列を宣言します`myArray`から派生した`CObArray`します。 配列が格納およびへのポインターを返す`CPerson`オブジェクト (ここ`CPerson`クラスから派生`CObject`)。 呼び出す`CObArray`メンバー関数、またはするには、新しいタイプ セーフを呼び出すことができます`GetAt`と`ElementAt`関数やタイプ セーフを使用して **[ ]** 演算子。

2 番目の例は、型付きポインター リストを宣言します`myList`から派生した`CPtrList`します。 リストが格納およびへのポインターを返す`MY_STRUCT`オブジェクト。 クラスに基づいて`CPtrList`から派生していないオブジェクトへのポインターを格納するために使用`CObject`します。 `CTypedPtrList` さまざまなタイプ セーフなメンバー関数: `GetHead`、 `GetTail`、 `RemoveHead`、 `RemoveTail`、 `GetNext`、 `GetPrev`、および`GetAt`します。

###  <a name="_core_typed.2d.pointer_map_usage"></a> 型指定されたポインターのマップの使用

型指定されたポインター マップ クラス[CTypedPtrMap](../mfc/reference/ctypedptrmap-class.md)、3 つのパラメーターを受け取ります。*BASE_CLASS*、*キー*、および*値*します。 *BASE_CLASS*パラメーターは、新しいクラスを派生元のクラスを指定します: `CMapPtrToWord`、 `CMapPtrToPtr`、 `CMapStringToPtr`、 `CMapWordToPtr`、`CMapStringToOb`など。 *キー*に似ていますが*キー*で`CMap`:これには、参照に使用されるキーの種類を指定します。 *値*に似ていますが*値*で`CMap`:これには、マップに格納されているオブジェクトの種類を指定します。 例:

[!code-cpp[NVC_MFCCollections#6](../mfc/codesnippet/cpp/template-based-classes_6.cpp)]

最初の例は、マップに基づく`CMapPtrToPtr`: を使用して`CString`へのポインターへのマップ キー`MY_STRUCT`します。 タイプ セーフを呼び出すことによって格納されたポインターを検索できます`Lookup`メンバー関数。 使用することができます、 **[ ]** 演算子に格納されているポインターを検索し、追加することがない場合。 タイプ セーフを使用してマップを反復処理できると`GetNextAssoc`関数。 呼び出すこともできます他のメンバー関数はクラスの`CMapPtrToPtr`します。

2 番目の例に基づくマップは、 `CMapStringToOb` — ストアド ポインターにマップされている文字列のキーを使用して`CMyObject`オブジェクト。 クラスのメンバーを呼び出すことができます、前の段落で説明されている同じタイプ セーフなメンバーを使用する、または`CMapStringToOb`します。

> [!NOTE]
>  指定した場合、**クラス**または**構造体**の入力、*値*ポインターや、型、クラスまたは構造体への参照ではなく、パラメーターには、コピー コンス トラクターを持つ必要があります。

詳細については、次を参照してください。[タイプ セーフなコレクションを作成する方法](../mfc/how-to-make-a-type-safe-collection.md)します。

## <a name="see-also"></a>関連項目

[コレクション](../mfc/collections.md)
