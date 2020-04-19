---
title: retval (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.retval
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
ms.openlocfilehash: 2a2865c1eda229f1a2fcd457c22119b2908c1caa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514049"
---
# <a name="retval"></a>retval

メンバーの戻り値を受け取るパラメーターを指定します。

## <a name="syntax"></a>構文

```cpp
[retval]
```

## <a name="remarks"></a>Remarks

**Retval** C++属性には、 [retval](/windows/win32/Midl/retval) MIDL 属性と同じ機能があります。

**retval**は、関数の宣言の最後の引数に指定されている必要があります。

## <a name="example"></a>例

**Retval**の使用例については、[バインド](bindable.md)可能なの例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|インターフェイスパラメーター、インターフェイスメソッド|
|**反復可能**|いいえ|
|**必要な属性**|**out**|
|**無効な属性**|**in**|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[パラメーター属性](parameter-attributes.md)<br/>
[メソッド属性](method-attributes.md)