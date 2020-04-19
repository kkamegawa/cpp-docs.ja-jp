---
title: raw_property_prefixes import 属性
ms.date: 08/29/2019
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: d4d91470781e7c5f673fd228c24904322d1db8b3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216040"
---
# <a name="raw_property_prefixes-import-attribute"></a>raw_property_prefixes import 属性

**C++のみ**

3 つのプロパティ メソッドの代替プレフィックスを指定します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***raw_property_prefixes (** "*getprefix*" **,** "*putprefix*" **,** "*putrefprefix*" **)**

### <a name="parameters"></a>パラメーター

*GetPrefix*\
`propget`メソッドに使用するプレフィックス。

*PutPrefix*\
`propput`メソッドに使用するプレフィックス。

*PutRefPrefix*\
`propputref`メソッドに使用するプレフィックス。

## <a name="remarks"></a>Remarks

既定では、低レベル`propget`の`propput`、、 `propputref`およびの各メソッドは、それぞれ`put_`、、および`get_` `putref_`のプレフィックスを使用して名前が付けられたメンバー関数によって公開されます。 これらのプレフィックスは、MIDL によって生成されるヘッダー ファイルで使用される名前と互換性があります。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
