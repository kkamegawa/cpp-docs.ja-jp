---
title: '&lt;hash_map&gt;'
ms.date: 01/18/2018
f1_keywords:
- <hash_map>
- std::<hash_map>
helpviewer_keywords:
- hash_map header
ms.openlocfilehash: 6bb2ca0cc14bcc4a9b9df9877902de9181e0a768
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77258147"
---
# <a name="lthash_mapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> このヘッダーは廃止され、互換性のために残されています。 代替手段は[> unordered_map\<](unordered-map.md)です。

コンテナークラステンプレート hash_map と hash_multimap と、そのサポートテンプレートを定義します。

## <a name="syntax"></a>構文

```cpp
#include <hash_map>
```

### <a name="operators"></a>演算子

|hash_map バージョン|hash_multimap バージョン|説明|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_map)](hash-map-operators.md#op_neq)|[operator! = (hash_multimap)](hash-map-operators.md#op_neq_mm)|演算子の左側の hash_map または hash_multimap オブジェクトが右側の hash_map または hash_multimap オブジェクトと等しくないかどうかをテストします。|
|[operator== (hash_map)](hash-map-operators.md#op_eq_eq)|[operator== (hash_multimap)](hash-map-operators.md#op_eq_eq_mm)|演算子の左側の hash_map または hash_multimap オブジェクトが右側の hash_map または hash_multimap オブジェクトと等しいかどうかをテストします。|

### <a name="specialized-template-functions"></a>特殊テンプレート関数

|hash_map バージョン|hash_multimap バージョン|説明|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|2 つの hash_map または hash_multimap の要素を交換します。|

### <a name="classes"></a>クラス

|クラス|説明|
|-|-|
|[hash_compare クラス](hash-compare-class.md)|ハッシュ連想コンテナー (hash_map、hash_multimap、hash_set、または hash_multiset) のいずれかで使用できるオブジェクトを記述します。これは、格納されている要素の順序付けおよびハッシュを行う既定の `Traits` パラメーターオブジェクトとして使用できます。|
|[value_compare クラス](value-compare-class.md)|要素のキーの値を比較し、要素の hash_map 内の相対順序を決定して、hash_map の要素を比較できる関数オブジェクトを提供します。|
|[hash_map クラス](hash-map-class.md)|一意の並べ替えキーとそれに関連付けられている値のペアを要素として持つコレクションのデータを格納したり、迅速に取得したりするために使用されます。|
|[hash_multimap クラス](hash-multimap-class.md)|必ずしも一意ではない並べ替えキーとそれに関連付けられている値のペアを要素として持つコレクションのデータを格納したり、迅速に取得したりするために使用されます。|

## <a name="requirements"></a>要件

**ヘッダー:** \<hash_map >

**名前空間:** stdext

## <a name="see-also"></a>参照

[ヘッダー ファイル リファレンス](cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](cpp-standard-library-reference.md)
