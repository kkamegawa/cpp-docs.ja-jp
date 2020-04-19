---
title: raw_native_types import 属性
ms.date: 08/29/2019
f1_keywords:
- raw_native_types
helpviewer_keywords:
- raw_native_types attribute
ms.assetid: 9f38daa8-8dc0-46a5-aff9-f1ff9c1e6f48
ms.openlocfilehash: eb08a8e7cb081bd7a470c3c1ecf1492a7a65f833
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216072"
---
# <a name="raw_native_types-import-attribute"></a>raw_native_types import 属性

**C++のみ**

高レベルのラッパー関数での COM サポートクラスの使用を無効にし、代わりに下位レベルのデータ型を強制的に使用します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***raw_native_types**

## <a name="remarks"></a>Remarks

既定では、高レベルのエラー処理メソッドは、 `BSTR`および`VARIANT`データ型と生の com インターフェイスポインターの代わりに、com サポートクラス[_bstr_t](../cpp/bstr-t-class.md)と[_variant_t](../cpp/variant-t-class.md)を使用します。 これらのクラスは、これらのデータ型のメモリ ストレージの割り当てと解放の詳細情報をカプセル化し、型キャストと変換演算を大幅に簡略化します。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
