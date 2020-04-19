---
title: '方法: タイプ セーフなコレクションを作成します。'
ms.date: 11/04/2016
helpviewer_keywords:
- type-safe collections [MFC]
- serializing collection-class elements [MFC]
- collection classes [MFC], type safety
- SerializeElements function [MFC]
- collection classes [MFC], template-based
- serialization [MFC], collection classes
- collection classes [MFC], deriving from nontemplate
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
ms.openlocfilehash: c8be781bad699edb8cb0be844d79802269c3e0c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160264"
---
# <a name="how-to-make-a-type-safe-collection"></a>方法: タイプ セーフなコレクションを作成します。

この記事では、独自のデータ型のタイプ セーフなコレクションを作成する方法について説明します。 ここでは、次の内容について説明します。

- [テンプレート ベースのクラスを使用して、タイプ セーフ](#_core_using_template.2d.based_classes_for_type_safety)

- [ヘルパー関数を実装します。](#_core_implementing_helper_functions)

- [非テンプレート コレクション クラスを使用します。](#_core_using_nontemplate_collection_classes)

Microsoft Foundation Class ライブラリでは、C++ テンプレートに基づく定義済みのタイプ セーフなコレクションを提供します。 テンプレートがいるため、これらのクラスはタイプ セーフと型キャストし、この目的の非テンプレート クラスの使用に関連するその他の追加作業なしの使いやすさを提供に役立ちます。 MFC サンプル[収集](../overview/visual-cpp-samples.md)MFC アプリケーションのテンプレート ベースのコレクション クラスの使用方法を示します。 一般に、新しいコレクションのコードを作成するときのこれらのクラスを使用します。

##  <a name="_core_using_template.2d.based_classes_for_type_safety"></a> テンプレート ベースのクラスを使用して、タイプ セーフ

#### <a name="to-use-template-based-classes"></a>テンプレート ベースのクラスを使用するには

1. コレクション クラスの型の変数を宣言します。 例:

   [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_1.cpp)]

1. メンバーのコレクション オブジェクトの関数を呼び出します。 例:

   [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_2.cpp)]

1. 必要に応じて、実装、[ヘルパー関数](../mfc/reference/collection-class-helpers.md)と[SerializeElements](../mfc/reference/collection-class-helpers.md#serializeelements)します。 これらの関数を実装する方法の詳細については、次を参照してください。[ヘルパー関数を実装する](#_core_implementing_helper_functions)します。

この例では、整数のリストの宣言を示します。 手順 1 の最初のパラメーターでは、リストの要素として格納されているデータの種類です。 2 番目のパラメーター データを指定する方法に渡されるなど、コレクション クラスのメンバー関数から返す`Add`と`GetAt`します。

##  <a name="_core_implementing_helper_functions"></a> ヘルパー関数を実装します。

テンプレート ベースのコレクション クラス`CArray`、 `CList`、および`CMap`派生コレクション クラスの必要に応じてカスタマイズできる 5 つのグローバルなヘルパー関数を使用します。 これらのヘルパー関数については、次を参照してください。[コレクション クラスのヘルパー](../mfc/reference/collection-class-helpers.md)で、 *MFC リファレンス*します。 シリアル化の関数の実装では、テンプレート ベースのコレクション クラスのほとんどの用途の必要があります。

###  <a name="_core_serializing_elements"></a> 要素をシリアル化します。

`CArray`、 `CList`、および`CMap`クラスの呼び出し`SerializeElements`にコレクション要素を保存またはアーカイブから読み取ります。

既定の実装、`SerializeElements`ヘルパー関数は、ビットごとの書き込みをオブジェクトから、アーカイブには、またはビットごとのオブジェクトが格納されているかどうかに応じて、オブジェクトに、アーカイブからの読み取りまたはアーカイブから取得します。 オーバーライド`SerializeElements`このアクションが適切でない場合。

コレクションから派生したオブジェクトを格納する場合`CObject`を使用して、`IMPLEMENT_SERIAL`マクロ コレクション要素クラスの実装に組み込まれたシリアル化機能の利点にかかる`CArchive`と`CObject`:

[!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_3.cpp)]

オーバー ロードされた挿入演算子`CArchive`呼び出す`CObject::Serialize`(またはその関数のオーバーライド) 各`CPerson`オブジェクト。

##  <a name="_core_using_nontemplate_collection_classes"></a> 非テンプレート コレクション クラスを使用します。

MFC には、MFC バージョン 1.0 で導入されたコレクション クラスもサポートしています。 これらのクラスは、テンプレートには基づいていません。 サポートされる型のデータを含めるために使用できる、 `CObject*`、 `UINT`、 `DWORD`、および`CString`します。 これらの定義済みのコレクションを使用することができます (など`CObList`) から派生した任意のオブジェクトのコレクションを保持するために`CObject`します。 MFC は、その他の定義済みのコレクションなどのプリミティブ型を保持するためにも用意されています。`UINT`ポインターを無効にすると (`void`*)。 一般に、ただしは多くの場合、固有のクラスとその派生クラスのオブジェクトを保持するために、独自のタイプ セーフなコレクションを定義すると便利です。 テンプレートに基づいていないコレクション クラスでこれは、テンプレートに基づくクラスを使用してより多くの作業です。

非テンプレート コレクションでタイプ セーフなコレクションを作成する 2 つの方法はあります。

1. 型キャストは必要な場合に、非テンプレート コレクションを使用します。 これより簡単な方法です。

1. 派生し、非テンプレート タイプ セーフのコレクションを拡張します。

#### <a name="to-use-the-nontemplate-collections-with-type-casting"></a>型キャストを使用したテンプレートのコレクションを使用するには

1. 非テンプレート クラスのいずれかのような使用`CWordArray`、直接します。

   たとえば、作成、`CWordArray`に任意の 32 ビット値を追加し、それらを取得します。 やるべきものがありません。 定義済みの機能を使用するだけです。

   など、定義済みのコレクションを使用することもできます。`CObList`から派生した任意のオブジェクトを保持するために、`CObject`します。 A`CObList`へのポインターを保持するためにコレクションが定義されている`CObject`します。 一覧からオブジェクトを取得するときに、結果から適切な型をキャストする必要があります、`CObList`関数へのポインターを返す`CObject`します。 格納する場合など、`CPerson`内のオブジェクトを`CObList`コレクションへのポインターを取得した要素をキャストする必要がある、`CPerson`オブジェクト。 次の例では、`CObList`を保持するコレクション`CPerson`オブジェクト。

   [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_4.cpp)]

   この手法の定義済みのコレクション型を使用して、必要に応じてキャストは、さまざまなコレクションのニーズのための適切な可能性があります。 さらに機能または複数のタイプ セーフが必要な場合、テンプレートに基づくクラスを使用して、または、次の手順に従います。

#### <a name="to-derive-and-extend-a-nontemplate-type-safe-collection"></a>派生および非テンプレート タイプ セーフなコレクションを拡張するには

1. 定義済みの非テンプレート クラスのいずれかから、独自のコレクション クラスを派生します。

   クラスを派生するときは、既存の関数にタイプ セーフなインターフェイスを提供するタイプ セーフ ラッパー関数を追加できます。

   たとえば、次の一覧からの派生`CObList`を保持する`CPerson`オブジェクトの場合、ラッパー関数を追加する場合があります`AddHeadPerson`と`GetHeadPerson`以下に示すように。

   [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/cpp/how-to-make-a-type-safe-collection_5.h)]

   これらのラッパー関数を追加および取得するタイプ セーフな方法を提供する`CPerson`オブジェクト派生しますから。 ことを確認、`GetHeadPerson`関数、型キャスト カプセル化するだけです。

   タイプ セーフ ラッパーで既存の機能をラップするだけではなく、コレクションの機能を拡張する新しい関数の定義によって新しい機能を追加することもできます。 たとえば、この記事[CObject コレクションのすべてのオブジェクトを削除する](../mfc/deleting-all-objects-in-a-cobject-collection.md)をリストに含まれるすべてのオブジェクトを削除する関数を記述します。 この関数は、メンバー関数として、派生クラスに追加でした。

## <a name="see-also"></a>関連項目

[コレクション](../mfc/collections.md)
