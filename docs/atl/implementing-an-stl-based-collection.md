---
title: C++ 標準ライブラリに基づくコレクションを実装します。
ms.date: 11/04/2016
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
ms.openlocfilehash: 609ec2547cf7a8ab93ef757f7a8e460542c9de28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197498"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>C++ 標準ライブラリに基づくコレクションを実装します。

ATL には、`ICollectionOnSTLImpl`迅速に、オブジェクトのコレクションの C++ 標準ライブラリに基づくインターフェイスを実装することを有効にするインターフェイス。 このクラスの動作を理解するのには、オートメーション クライアントを目的とした、読み取り専用コレクションを実装するこのクラスを使用する簡単な例 (下記) を使用します。

サンプルのコードは、 [ATLCollections サンプル](../overview/visual-cpp-samples.md)します。

この手順を完了するには、ことができます。

- [新しい単純なオブジェクトを生成](#vccongenerating_an_object)します。

- [IDL ファイルを編集](#vcconedit_the_idl)生成されるインターフェイス。

- [5 つの typedef を作成する](#vcconstorage_and_exposure_typedefs)コレクション アイテムの格納方法と、COM インターフェイスを使用してクライアントの公開方法について説明します。

- [ポリシー クラスを作成するには、コピー用の 2 つの typedef](#vcconcopy_classes)します。

- [作成、列挙子とコレクションの実装の typedef](#vcconenumeration_and_collection)します。

- [コレクションの typedef を使用するウィザードで生成された C++ コードを編集](#vcconedit_the_generated_code)します。

- [コレクションを設定するコードを追加](#vcconpopulate_the_collection)します。

##  <a name="vccongenerating_an_object"></a> 新しい単純なオブジェクトを生成します。

アプリケーション設定 属性 ボックスがオフになっていることを確認、新しいプロジェクトを作成します。 クラスの追加 ダイアログ ボックスを使用して、単純なオブジェクトを生成するシンプル オブジェクト ウィザードの追加と呼ばれる`Words`します。 デュアル インターフェイスと呼ばれることを確認`IWords`が生成されます。 生成されたクラスのオブジェクトは、単語 (つまり、文字列) のコレクションを表すため使用されます。

##  <a name="vcconedit_the_idl"></a> IDL ファイルの編集

次に、IDL ファイルを開くし、有効にするために必要な 3 つのプロパティを追加`IWords`を読み取り専用コレクション インターフェイスは、次に示すようにします。

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

これは、オートメーション クライアントを念頭に設計された読み取り専用コレクション インターフェイスの標準形式です。 このインターフェイスの定義内の番号付きコメントは、次のコメントに対応しています。

1. オートメーション クライアントにアクセスするため、コレクション インターフェイスがデュアル、通常は、`_NewEnum`プロパティを使用して`IDispatch::Invoke`します。 ただし、オートメーション クライアントは、デュアル インターフェイスがディスパッチ インターフェイスに適していますので、vtable を使用して残りのメソッドをアクセスできます。

1. 実行時にインターフェイスをデュアルまたはディスパッチ インターフェイスを拡張するがいない場合 (つまり、追加のメソッドまたはを使用してプロパティを提供しません`IDispatch::Invoke`)、適用する必要があります、 **nonextensible**属性の定義にします。 この属性には、コンパイル時に完全なコードの検証を実行するオートメーション クライアントが使用できます。 この場合は、インターフェイスを拡張しません。

1. DISPID を正しくは、このプロパティを使用できるオートメーション クライアントの場合に重要です。 (なに 1 つだけのアンダー スコアがあることに注意してください)。

1. DISPID として任意の値を指定することができます、`Item`プロパティ。 ただし、`Item`通常 DISPID_VALUE をコレクションの既定のプロパティを使用します。 これにより、オートメーション クライアントを明示的に名前を指定せず、プロパティを参照してください。

1. 戻り値を使用するデータ型、`Item`プロパティが COM クライアントにとってはできる限り、コレクションに格納されている項目の種類。 インターフェイスは、ので、標準の COM 文字列型、BSTR を使用する必要があります、文字列を返します。 できますデータ保存する別の形式で内部的にすぐにわかります。

1. ように DISPID を使用する値、`Count`プロパティは、まったく任意です。 このプロパティの DISPID を標準はありません。

##  <a name="vcconstorage_and_exposure_typedefs"></a> 記憶域と露出の Typedef を作成します。

コレクション インターフェイスが定義されているデータを格納する方法と、列挙子を使用して、データを公開する方法を決定する必要があります。

これらの質問に対する回答は、新しく作成されたクラスのヘッダー ファイルの先頭付近にある追加することができますの typedef の数値の形式で指定できます。

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

この場合、としてデータを格納する、 **std::vector**の**std::string**秒。 **std::vector**はマネージ配列のように動作する C++ 標準ライブラリ コンテナー クラスです。 **std::string**は、C++ 標準ライブラリの文字列クラスです。 これらのクラスを簡単に文字列のコレクションを使用します。

列挙子がによって返される Visual Basic のサポートは、このインターフェイスの成功に不可欠であるため、`_NewEnum`プロパティをサポートする必要があります、`IEnumVARIANT`インターフェイス。 これは、Visual Basic で認識される唯一の列挙子インターフェイスです。

##  <a name="vcconcopy_classes"></a> コピー ポリシー クラスの Typedef を作成します。

これまでに作成した typedef は、さらに、列挙子とコレクションで使用されるコピー クラスの typedef を作成する必要があるすべての情報を提供します。

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

この例では、カスタムを使用することができます`GenericCopy`VCUE_Copy.h とから VCUE_CopyString.h で定義されているクラス、 [ATLCollections](../overview/visual-cpp-samples.md)サンプル。 このクラスは、その他のコードで使用できますが、それ以上の特殊化を定義する必要があります`GenericCopy`独自のコレクションで使用されるデータ型をサポートするためにします。 詳細については、次を参照してください。 [ATL コピー ポリシー クラス](../atl/atl-copy-policy-classes.md)します。

##  <a name="vcconenumeration_and_collection"></a> 列挙とコレクションの Typedef を作成します。

これでテンプレートに必要なパラメーターに特殊な`CComEnumOnSTL`と`ICollectionOnSTLImpl`typedef の形式でこのような状況のクラスが用意されています。 特化された型の使用を簡素化するには、次に示す 2 つの typedef を作成します。

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

今すぐ`CollectionType`の特殊化のシノニムです`ICollectionOnSTLImpl`を実装する、`IWords`インターフェイスは、以前に定義されをサポートする列挙子を提供`IEnumVARIANT`します。

##  <a name="vcconedit_the_generated_code"></a> ウィザードで生成されたコードの編集

派生する必要がありますので`CWords`によって表されるインターフェイスの実装から、 `CollectionType` typedef なく`IWords`以下に示すように。

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

##  <a name="vcconpopulate_the_collection"></a> コレクションを設定するコードを追加します。

残っていることだけは、データを持つベクトルを設定します。 この簡単な例では、クラスのコンス トラクター内のコレクションにいくつかの単語を追加できます。

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

ここで、任意のクライアントで、コードをテストできます。

## <a name="see-also"></a>関連項目

[コレクションと列挙子](../atl/atl-collections-and-enumerators.md)<br/>
[ATLCollections サンプル](../overview/visual-cpp-samples.md)<br/>
[ATL コピー ポリシー クラス](../atl/atl-copy-policy-classes.md)
