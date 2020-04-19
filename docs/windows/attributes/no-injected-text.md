---
title: no_injected_text (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 354643020e704a87daa2e56e923b6a0a704bf0b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409292"
---
# <a name="noinjectedtext"></a>no_injected_text

コンパイラがコードの属性を使用した結果として挿入するを防ぎます。

## <a name="syntax"></a>構文

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>パラメーター

*boolean*<br/>
(省略可能)**true** 、挿入されたコードが必要ない場合**false**挿入するコードを許可します。 **true**既定値です。

## <a name="remarks"></a>Remarks

最も一般的な用途、 **no_injected_text** C++属性は、 [/Fx](../../build/reference/fx-merge-injected-code.md)コンパイラ オプションは、挿入、 **no_injected_text**属性が .mrg ファイルにします。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|任意の場所|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[コンパイラ属性](compiler-attributes.md)