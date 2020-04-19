---
title: 方法 getlasterror (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: b14316bd929f4b41b13a76c41e94b31b7534e9d8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513885"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

この関数を呼び出したときにエラーが発生した場合に、呼び出し元がを呼び出し`GetLastError`てエラーコードを取得できることを呼び出し元に通知します。

## <a name="syntax"></a>構文

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Remarks

Has **getlasterror** C++属性に[は、すべて](/windows/win32/Midl/usesgetlasterror)の機能と同じ機能があります。

## <a name="example"></a>例

使用方法の例については、 [idl_module](idl-module.md)の例を**参照してください。**

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**module**属性|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)