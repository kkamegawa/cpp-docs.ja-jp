---
title: high_property_prefixes import 属性
ms.date: 08/29/2019
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: 9e44f6f1afae479f803f4c6d866ef3ee38744561
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219009"
---
# <a name="high_property_prefixes-import-attribute"></a>high_property_prefixes import 属性

**C++のみ**

3 つのプロパティ メソッドの代替プレフィックスを指定します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***high_property_prefixes (** "*getprefix*" **,** "*putprefix*" **,** "*putrefprefix*" **)**

### <a name="parameters"></a>パラメーター

*GetPrefix*\
`propget`メソッドに使用されるプレフィックス。

*PutPrefix*\
`propput`メソッドに使用されるプレフィックス。

*PutRefPrefix*\
`propputref`メソッドに使用されるプレフィックス。

## <a name="remarks"></a>Remarks

既定では、高レベルのエラー処理`propget`、 `propput`、および`propputref`メソッドは、それぞれプレフィックス`Get`、 `Put`、および`PutRef`を持つという名前のメンバー関数によって公開されます。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
