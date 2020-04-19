---
title: tlbid import 属性
ms.date: 08/29/2019
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: 364fb224b0f2769cb0933e71d18ff70768189328
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216540"
---
# <a name="tlbid-import-attribute"></a>tlbid import 属性

**C++のみ**

プライマリ タイプ ライブラリ以外のライブラリの読み込みを許可します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ-dll***tlbid (** *数値* **)**

### <a name="parameters"></a>パラメーター

*少数*\
*タイプライブラリ dll*内のタイプライブラリの番号。

## <a name="remarks"></a>Remarks

複数のタイプライブラリが1つの DLL に組み込まれている場合、 **tlbid**を使用してプライマリタイプライブラリ以外のライブラリを読み込むことができます。

例えば:

```cpp
#import <MyResource.dll> tlbid(2)
```

上の式は、下の式と同等です。

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
