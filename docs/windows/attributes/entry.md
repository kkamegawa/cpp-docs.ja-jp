---
title: entry (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: 71abf4f183255fa137b43ac9cabd88d15c3fc85d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490899"
---
# <a name="entry"></a>entry

DLL 内のエントリポイントを識別することによって、モジュール内のエクスポートされた関数または定数を指定します。

## <a name="syntax"></a>構文

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
エントリポイントの ID。

## <a name="remarks"></a>Remarks

**Entry** C++属性には、 [entry](/windows/win32/Midl/entry) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

**Entry**の使用例については、 [idl_module](idl-module.md)の例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|`idl_module` 属性|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)