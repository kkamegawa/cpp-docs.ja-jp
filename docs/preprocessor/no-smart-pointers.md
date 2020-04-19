---
title: no_smart_pointers import 属性
ms.date: 08/29/2019
f1_keywords:
- no_smart_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: 1fca3eb486ff3cfc7403c38e91855b799a698782
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220690"
---
# <a name="no_smart_pointers-import-attribute"></a>no_smart_pointers import 属性

**C++のみ**

タイプ ライブラリのすべてのインターフェイスに対して、スマート ポインターの作成を抑制します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***no_smart_pointers**

## <a name="remarks"></a>Remarks

既定では、`#import` を使用すると、タイプ ライブラリのすべてのインターフェイスのスマート ポインター宣言を取得できます。 これらのスマートポインターの種類は[_com_ptr_t](../cpp/com-ptr-t-class.md)です。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
