---
title: ATL のコレクションと列挙子
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collections, ATL classes
- enumerators, ATL classes
- collection interfaces
ms.assetid: b2d37119-3ab2-4e0a-b65b-f377f07e4098
ms.openlocfilehash: 502bedb1773dc2a6edbd6679d50e9c5946228283
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491896"
---
# <a name="atl-collections-and-enumerators"></a>ATL のコレクションと列挙子

`collection`は、データ項目のグループ (生データまたはその他のオブジェクト) へのアクセスを可能にするインターフェイスを提供する COM オブジェクトです。 オブジェクトのグループへのアクセスを提供するための標準に従うインターフェイスを、*コレクションインターフェイス*と呼びます。

コレクションインターフェイスは、少なくともコレクション内`Count`の項目数を返すプロパティ`Item` 、インデックスに基づいてコレクションから項目を返すプロパティ、および`_NewEnum`を返すプロパティを提供する必要があります。コレクションの列挙子。 必要に応じて`Add` `Remove` 、コレクションインターフェイスは、コレクションへの項目の挿入または削除を許可するメソッドと`Clear`メソッド、およびすべての項目を削除するメソッドを提供できます。

`enumerator`は、コレクション内の項目を反復処理するためのインターフェイスを提供する COM オブジェクトです。 `Next`列挙子インターフェイスは`Skip` `Clone`、、、、およびの4つの必須メソッドを使用して、コレクションの要素へのシリアルアクセスを提供します。 `Reset`

列挙子インターフェイスの詳細については、 [IEnumString](/windows/win32/api/objidl/nn-objidl-ienumstring)インターフェイスなどの参照コンテンツを参照してください。

## <a name="in-this-section"></a>このセクションの内容

[ATL のコレクションと列挙子クラス](../atl/atl-collection-and-enumerator-classes.md)<br/>
コレクションと列挙子の実装に役立つ ATL クラスへのリンクを簡単に説明し、提供します。

[コレクションと列挙子インターフェイスのデザインの原則](../atl/design-principles-for-collection-and-enumerator-interfaces.md)<br/>
各種類のインターフェイスの背後にあるさまざまな設計原則について説明します。

[C++ 標準ライブラリに基づくコレクションの実装](../atl/implementing-an-stl-based-collection.md)<br/>
C++標準ライブラリベースのコレクションの実装について説明する拡張された例。

## <a name="related-sections"></a>関連項目

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Active Template Library を使用してプログラミングする方法に関する概念説明のトピックへのリンクを提供します。

[ATLCollections サンプル](../overview/visual-cpp-samples.md)<br/>
`ICollectionOnSTLImpl` と`CComEnumOnSTL`の使用方法、およびカスタムコピーポリシークラスの実装方法を示すサンプル。

## <a name="see-also"></a>関連項目

[概念](../atl/active-template-library-atl-concepts.md)
