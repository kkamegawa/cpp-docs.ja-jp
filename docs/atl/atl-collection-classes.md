---
title: ATL コレクション クラス
ms.date: 11/19/2018
helpviewer_keywords:
- DestructElements function
- collection classes, choosing
- ConstructElements function
- SerializeElements function
- traits classes
- collection classes, about collection classes
- CTraits classes
- collection classes
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
ms.openlocfilehash: 70ca283468a51b4214273698a532ce2a85d52b44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223447"
---
# <a name="atl-collection-classes"></a>ATL コレクション クラス

ATL には、格納およびデータにアクセスするための多くのクラスが用意されています。 どのクラスを使用する場合など、いくつかの要因によって異なります。

- 格納されるデータの量

- データへのアクセスの効率とパフォーマンス

- インデックスまたはキーでデータにアクセスする機能

- データを並べ替える方法

- 個人的な好み

## <a name="small-collection-classes"></a>小規模なコレクション クラス

ATL は、少数のオブジェクトを処理するための次のような配列クラスを提供します。 ただし、これらのクラスが限定され、ATL で内部的に使用するために設計されました。 プログラムで使用することは推奨されません。

|クラス|データ ストレージの種類|
|-----------|--------------------------|
|[CSimpleArray](../atl/reference/csimplearray-class.md)|少数のオブジェクトを処理するため、配列クラスを実装します。|
|[CSimpleMap](../atl/reference/csimplemap-class.md)|少数のオブジェクトを処理するためのマッピング クラスを実装します。|

## <a name="general-purpose-collection-classes"></a>汎用コレクション クラス

以下のクラスは、配列、リスト、およびマップを実装し、コレクション クラスの一般的な目的として提供されます。

|クラス|データ ストレージの種類|
|-----------|--------------------------|
|[CAtlArray](../atl/reference/catlarray-class.md)|配列を実装します。|
|[CAtlList](../atl/reference/catllist-class.md)|リストを実装します。|
|[CAtlMap](../atl/reference/catlmap-class.md)|データを参照して、キーまたは値で、マップ構造体を実装します。|
|[CRBMap](../atl/reference/crbmap-class.md)|レッド ブラック アルゴリズムを使用して、マップの構造体を実装します。|
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|レッド ブラック マルチ マップの構造体を実装します。|

これらのクラスには、デバッグ ビルドで使用すると、多くのプログラミング エラーをトラップしますが、単純なパフォーマンスをこれらのチェックを行わない製品版ビルドで。

## <a name="specialized-collection-classes"></a>特殊なコレクション クラス

専門的なコレクション クラスは、メモリのポインターとインターフェイス ポインターを管理するためも示します。

|クラス|目的|
|-----------|-------------|
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|スマート ポインターの配列を構築するときに、便利なメソッドを提供します。|
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|スマート ポインターのリストを構築するときに、便利なメソッドを提供します。|
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|ストア`IUnknown`ポインターへのパラメーターとして使用するものでは、 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)テンプレート クラス。|
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|ヒープのポインターのリストを構築するときに、便利なメソッドを提供します。|
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|COM インターフェイス ポインターの配列を構築するときに、便利なメソッドを提供します。|
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|COM インターフェイス ポインターのリストを構築するときに、便利なメソッドを提供します。|

## <a name="choosing-a-collection-class"></a>コレクション クラスの選択

使用可能なコレクション クラスは、次の表に示すように、さまざまなパフォーマンス特性を提供します。

- 列 2 および 3 は、各クラスの順序付けと特性にアクセスします。 表に使用されている用語 "順序付け" とは、項目を挿入または削除した順によってコレクション内の項目の位置が決まることを意味します。項目がその内容によって並べ替えられることを意味するのではありません。 用語 "インデックス付き" は、通常の配列内の項目と同様に、コレクション内の項目を整数インデックスによって取得できることを意味します。

- 4 と 5 列には、各クラスのパフォーマンスについて説明します。 頻繁にコレクションに項目を挿入するアプリケーションでは、項目の挿入速度が特に重要です。他のアプリケーションでは、検索速度の方がより重要になる場合があります。

- 6 列目は、各形状で項目の重複が許可されるかどうかを表しています。

- 指定したコレクション クラスの操作のパフォーマンスは、コレクション内の要素の数、操作を完了するのに必要な時間の間のリレーションシップとして表現されます。 時間の長さにする操作は、線形に増加する要素の数は o (n) アルゴリズムとして説明します。 これに対し、一定な少なくなり、要素数が増えると増加する時間をする操作は O (log n) アルゴリズムとして説明します。 そのため、パフォーマンスの面で O (log n) アルゴリズム上回る数の要素が増えるとますます o (n) アルゴリズム。

### <a name="collection-shape-features"></a>コレクションの形状と特徴

|形式|順序あり|インデックスを作成|挿入します。<br /><br /> 要素|検索<br /><br /> 指定された要素|重複<br /><br /> 要素|
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|
|リスト|[はい]|いいえ|高速 (定数時間)|低速の o (n)|[はい]|
|配列|[はい]|Int (定数時間) で|最後に挿入する場合を除く低速の o (n)|低速の o (n)|[はい]|
|マップ|いいえ|キー (定数時間)|高速 (定数時間)|高速 (定数時間)|いいえ (キー)、はい (値)|
|レッド ブラック マップ|[はい] (キー) を|キーの O (log n)|高速の O (log n)|高速の O (log n)|いいえ|
|レッド ブラック Multimap|[はい] (キー) を|キー O(log n) (キーごとの複数の値) に|高速の O (log n)|高速の O (log n)|[はい] (キーごとの複数の値)|

## <a name="using-ctraits-objects"></a>CTraits オブジェクトを使用します。

広範囲のユーザー定義データ型を格納する、ATL コレクション クラスを使用することができます、比較などの重要な機能をオーバーライドすることができます。 CTraits クラスを使用してこれが実現されます。

CTraits クラスに似ていますが、柔軟性よりも、MFC コレクション クラスのヘルパー関数です。参照してください[コレクション クラスのヘルパー](../mfc/reference/collection-class-helpers.md)詳細についてはします。

コレクション クラスを構築するときに、CTraits クラスを指定するオプションがあります。 このクラスは、コレクション クラスを構成する他のメソッドが呼び出されたときに、比較などの操作を実行するコードが格納されます。 たとえば、リスト オブジェクトに独自のユーザー定義構造体が含まれている場合のみ特定のメンバー変数を比較する等値テストを再定義する可能性があります。 この方法では、リスト オブジェクトの Find メソッドをさらに便利な方法で動作します。

## <a name="example"></a>例

### <a name="code"></a>コード

[!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]

## <a name="comments"></a>コメント

CTraits クラスの一覧は、次を参照してください。[コレクション クラス](../atl/collection-classes.md)します。

次の図は、CTraits クラスのクラス階層を示します。

![コレクション クラス特徴階層構造](../atl/media/vctraitscollectionclasseshierarchy.gif "コレクション クラス特徴階層構造")

## <a name="collection-classes-samples"></a>コレクション クラスのサンプル

次のサンプルは、コレクション クラスを示しています。

- [MMXSwarm サンプル](../overview/visual-cpp-samples.md)

- [DynamicConsumer サンプル](../overview/visual-cpp-samples.md)

- [UpdatePV サンプル](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

- [マーキーのサンプル](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>関連項目

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[コレクション クラス](../atl/collection-classes.md)
