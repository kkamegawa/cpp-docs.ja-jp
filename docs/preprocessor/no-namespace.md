---
title: no_namespace import 属性
ms.date: 08/29/2019
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: ba52aed69cdbb46c135e6de5078d718e93f99c87
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220731"
---
# <a name="no_namespace-import-attribute"></a>no_namespace import 属性

**C++のみ**

コンパイラが名前空間名を生成しないことを指定します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***no_namespace**

## <a name="remarks"></a>Remarks

`#import` ヘッダー ファイルのタイプ ライブラリの内容は、通常、特定の名前空間で定義されます。 名前空間の名前は、元`library`の IDL ファイルのステートメントで指定します。 **No_namespace**属性が指定されている場合、この名前空間はコンパイラによって生成されません。

別の名前空間名を使用する場合は、代わりに[rename_namespace](../preprocessor/rename-namespace.md)属性を使用します。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
