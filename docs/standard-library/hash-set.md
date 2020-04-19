---
title: '&lt;hash_set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <hash_set>
- std::<hash_set>
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
ms.openlocfilehash: 00ca476816213d38b3c50c64e0978e65ac1a5ea1
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687945"
---
# <a name="lthash_setgt"></a>&lt;hash_set&gt;

> [!NOTE]
> このヘッダーは廃止され、互換性のために残されています。 代わりに、[<unordered_set>](../standard-library/unordered-set.md) を使用してください。

コンテナークラステンプレート hash_set と hash_multiset、およびそのサポートテンプレートを定義します。

## <a name="syntax"></a>構文

```cpp
#include <hash_set>
```

## <a name="remarks"></a>Remarks

### <a name="operators"></a>演算子

|Hash_set バージョン|Hash_multiset バージョン|説明|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_set)](../standard-library/hash-set-operators.md#op_neq)|[operator!= (hash_multiset)](../standard-library/hash-set-operators.md#op_neq)|演算子の左側の hash_set または hash_multiset オブジェクトが右側の hash_set または hash_multiset オブジェクトと等しくないかどうかをテストします。|
|[operator== (hash_set)](../standard-library/hash-set-operators.md#op_eq_eq)|[operator== (hash_multiset)](../standard-library/hash-set-operators.md#op_eq_eq)|演算子の左側の hash_set または hash_multiset オブジェクトが右側の hash_set または hash_multiset オブジェクトと等しいかどうかをテストします。|

### <a name="specialized-template-functions"></a>特殊テンプレート関数

|Hash_set バージョン|Hash_multiset バージョン|説明|
|-----------------------|----------------------------|-----------------|
|[swap (hash_set)](../standard-library/hash-set-functions.md#swap)|[swap (hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|2 つの hash_set または hash_multiset の要素を交換します。|

### <a name="classes"></a>クラス

|インスタンス|説明|
|-|-|
|[hash_compare クラス](../standard-library/hash-compare-class.md)|ハッシュ連想コンテナー (hash_map、hash_multimap、hash_set、または hash_multiset) のいずれかで使用できるオブジェクトを記述します。これは、既定の `Traits` パラメーターオブジェクトとして、含まれる要素の順序付けおよびハッシュを行います。|
|[hash_set クラス](../standard-library/hash-set-class.md)|コレクションのデータを格納し、迅速に取得するために使用されます。このコレクションに含まれる要素の値は一意で、キー値として機能します。|
|[hash_multiset クラス](../standard-library/hash-multiset-class.md)|コレクションのデータを格納し、迅速に取得するために使用されます。このコレクションに含まれる要素の値は一意で、キー値として機能します。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
