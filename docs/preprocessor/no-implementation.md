---
title: no_implementation import 属性
ms.date: 08/29/2019
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 8f0a7454fdbedc1959b665ccb2a23748d21c342d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220773"
---
# <a name="no_implementation-import-attribute"></a>no_implementation import 属性

**C++のみ**

ラッパーメンバー関数の実装`.tli`を含むヘッダーの生成を抑制します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***no_implementation**

## <a name="remarks"></a>Remarks

この属性が指定さ`.tlh`れている場合は、ヘッダーファイルをインクルード`.tli`する`#include`ステートメントを使用せずに、タイプライブラリ項目を公開する宣言を含むヘッダーが生成されます。

この属性は、 [implementation_only](../preprocessor/implementation-only.md)と組み合わせて使用されます。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
