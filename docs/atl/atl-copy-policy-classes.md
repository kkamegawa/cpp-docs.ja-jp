---
title: ATL コピー ポリシー クラス
ms.date: 11/04/2016
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
ms.openlocfilehash: 73bec31b4ae140797c85a06ee7c5023c9e0c4446
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252218"
---
# <a name="atl-copy-policy-classes"></a>ATL コピー ポリシー クラス

コピー ポリシー クラスが[ユーティリティ クラス](../atl/utility-classes.md)の初期化に使用すると、コピー、およびデータを削除します。 コピー ポリシー クラスでは、あらゆる種類のデータのコピーのセマンティクスを定義して、別のデータ型の間の変換を定義できます。

次のテンプレートの実装で ATL はコピー ポリシー クラス:

- [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)

- [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)

- [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)

テンプレート引数として渡すことができるコピー ポリシー クラスのデータ コピーまたは変換に必要な情報をカプセル化してこれらのクラスの極端な再利用性の ATL 開発者が用意されています。 たとえば、任意の任意のデータ型を使用してコレクションを実装する必要がある場合を提供する必要があるすべてが適切なコピー ポリシーありません、コレクションを実装するコードを操作する必要があるとします。

## <a name="definition"></a>定義

定義上、次の静的関数を提供するクラスはコピー ポリシー クラスは。

`static void init(` `DestinationType` `* p);`

`static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`

`static void destroy(` `DestinationType` `* p);`

型を置き換えることができます`DestinationType`と*SourceType*コピー ポリシーごとに任意のデータ型。

> [!NOTE]
>  任意のデータの種類のコピー ポリシー クラスを定義できますが、ATL コードのクラスの使用は、意味のある種類を制限する必要があります。 たとえば、コピーのポリシーを使用して class ATL のコレクションまたは列挙子の実装で`DestinationType`COM インターフェイスのメソッドのパラメーターとして使用できる型でなければなりません。

使用**init** 、データを初期化するために**コピー**データのコピーと**破棄**データを解放します。 初期化の正確な意味、コピー、および破棄は、コピー ポリシー クラスのドメインとは関連するデータ型によって異なります。

使用とコピー ポリシー クラスの実装の 2 つの要件があります。

- 最初のパラメーター**コピー**を使用して初期化されたデータへのポインターを受け取る必要がありますのみ**init**します。

- **破棄**を使用して初期化されたデータへのポインターを受け取る必要がありますのみ**init**または経由でコピーした**コピー**します。

## <a name="standard-implementations"></a>標準的な実装

ATL には、2 つのコピー ポリシー クラスの形式で、`_Copy`と`_CopyInterface`テンプレート クラス。

- `_Copy`クラスを同種のコピーのみ使用できます (データ型の間で変換ではない) 両方を指定する 1 つのテンプレート パラメーターのみ提供していますので`DestinationType`と*SourceType*します。 このテンプレートの汎用の実装が初期化または破棄コードが含まれていない、使用して`memcpy`データをコピーします。 ATL は、の特殊化も用意されています。`_Copy`のバリアント、LPOLESTR、OLEVERB、および CONNECTDATA のデータ型。

- `_CopyInterface`クラスは、標準の COM 規則に従ってインターフェイス ポインターのコピーの実装を提供します。 もう一度このクラスは、同種のコピーのみ、単純な代入とへの呼び出しを使用して`AddRef`コピーを実行します。

## <a name="custom-implementations"></a>カスタムの実装

通常、異機種混在環境 (つまり、データ型間の変換) をコピーするための独自コピー ポリシー クラスを定義する必要があります。 カスタム コピー ポリシー クラスの例については、見て VCUE_Copy.h VCUE_CopyString.h 内のファイル、 [ATLCollections](../overview/visual-cpp-samples.md)サンプル。 これらのファイルには、2 つのテンプレートのコピー ポリシー クラスが含まれて`GenericCopy`と`MapCopy`、数多くの特殊化の`GenericCopy`のさまざまなデータ型。

### <a name="genericcopy"></a>GenericCopy

`GenericCopy` 指定することができます、 *SourceType*と`DestinationType`テンプレート引数として。 最も一般的な形式を次に示します、 `GenericCopy` VCUE_Copy.h からクラス。

[!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]

VCUE_Copy.h には、このクラスの次の特殊化も含まれています: `GenericCopy<BSTR>`、 `GenericCopy<VARIANT, BSTR>`、`GenericCopy<BSTR, VARIANT>`します。 VCUE_CopyString.h にはからコピーするための特殊化が含まれています**std::string**s: `GenericCopy<std::string>`、 `GenericCopy<VARIANT, std::string>`、および`GenericCopy<BSTR, std::string>`します。 強化でした`GenericCopy`さらに、独自の特殊化を提供することで。

### <a name="mapcopy"></a>MapCopy

`MapCopy` マップ データを格納し、先の型の種類を指定することができますので、C++ 標準ライブラリ型マップにコピーするデータが格納されたと仮定します。 クラスの実装によって提供される typedef を使用した、 *MapType*クラスをソース データの種類を決定し、適切な呼び出しを`GenericCopy`クラス。 このクラスの特殊化は必要ありません。

[!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリに基づくコレクションの実装](../atl/implementing-an-stl-based-collection.md)<br/>
[ATLCollections サンプル](../overview/visual-cpp-samples.md)
