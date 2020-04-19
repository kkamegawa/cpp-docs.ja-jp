---
title: raw_interfaces_only import 属性
ms.date: 08/29/2019
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: 4b79aa4dbafa204d84f4d6ed7ec78fdec1b81fa7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216212"
---
# <a name="raw_interfaces_only-import-attribute"></a>raw_interfaces_only import 属性

**C++のみ**

エラー処理ラッパー関数、およびそれらのラッパー関数を使用する[プロパティ](../cpp/property-cpp.md)宣言を生成しません。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***raw_interfaces_only**

## <a name="remarks"></a>Remarks

また、 **raw_interfaces_only**属性により、非プロパティ関数の名前付けに使用される既定のプレフィックスも削除されます。 通常、プレフィックスは`raw_`です。 この属性が指定されている場合、関数名はタイプライブラリから直接取得されます。

この属性を使用することで、タイプ ライブラリの低水準の内容のみを公開できます。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
