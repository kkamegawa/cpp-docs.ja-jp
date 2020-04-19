---
title: _variant_t クラス
ms.date: 11/04/2016
f1_keywords:
- _variant_t
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
ms.openlocfilehash: 69976cab9caed653a8278f80821569b613f690eb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165951"
---
# <a name="variantt-class"></a>_variant_t クラス

**Microsoft 固有の仕様**

A **_variant_t**オブジェクトによってカプセル化、`VARIANT`データ型。 クラスがリソースの割り当てと解放を管理し、関数の呼び出し`VariantInit`と`VariantClear`に応じて。

### <a name="construction"></a>構築

|||
|-|-|
|[_variant_t](../cpp/variant-t-variant-t.md)|構築、 **_variant_t**オブジェクト。|

### <a name="operations"></a>操作

|||
|-|-|
|[Attach](../cpp/variant-t-attach.md)|アタッチを`VARIANT`オブジェクトを **_variant_t**オブジェクト。|
|[クリア](../cpp/variant-t-clear.md)|カプセル化されたクリア`VARIANT`オブジェクト。|
|[ChangeType](../cpp/variant-t-changetype.md)|型を変更、 **_variant_t**オブジェクトを指定された`VARTYPE`します。|
|[Detach](../cpp/variant-t-detach.md)|カプセル化されたデタッチ`VARIANT`オブジェクトからこの **_variant_t**オブジェクト。|
|[SetString](../cpp/variant-t-setstring.md)|これに文字列を割り当てます **_variant_t**オブジェクト。|

### <a name="operators"></a>演算子

|||
|-|-|
|[演算子 =](../cpp/variant-t-operator-equal.md)|既存の新しい値を割り当てます **_variant_t**オブジェクト。|
|[演算子 = =、! =](../cpp/variant-t-relational-operators.md)|比較する 2 つ **_variant_t**等値または非等値オブジェクトです。|
|[エクス トラクター](../cpp/variant-t-extractors.md)|カプセル化されたデータを抽出`VARIANT`オブジェクト。|

**Microsoft 固有の仕様はここまで**

## <a name="requirements"></a>必要条件

**Header:** \<comutil.h >

**Lib:** comsuppw.lib または comsuppwd.lib (詳細は「[/Zc:wchar_t (wchar_t をネイティブ型として認識)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)」を参照してください)

## <a name="see-also"></a>関連項目

[コンパイラ COM サポート クラス](../cpp/compiler-com-support-classes.md)