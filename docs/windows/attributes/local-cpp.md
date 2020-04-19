---
title: local (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.local
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
ms.openlocfilehash: 853331ce191f8fe41d5967d2d625a3dac8543a4d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514418"
---
# <a name="local-c"></a>local (C++)

インターフェイスヘッダーで使用すると、MIDL コンパイラをヘッダージェネレーターとして使用できるようになります。 個々の関数で使用する場合は、スタブが生成されないローカルプロシージャを指定します。

## <a name="syntax"></a>構文

```cpp
[local]
```

## <a name="remarks"></a>Remarks

**ローカル** C++属性には、[ローカル](/windows/win32/Midl/local)の MIDL 属性と同じ機能があります。

## <a name="example"></a>例

**ローカル**の使用方法の例については、「 [call_as](call-as.md) 」を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**インターフェイス**、インターフェイスメソッド|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|`dispinterface`|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[call_as](call-as.md)