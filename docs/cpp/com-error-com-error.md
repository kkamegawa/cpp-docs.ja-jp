---
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 8856289605cce430fdab36d6e3e8b743190e02ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155125"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error

**Microsoft 固有の仕様**

構築、 **_com_error**オブジェクト。

## <a name="syntax"></a>構文

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>パラメーター

*hr*<br/>
HRESULT 情報。

*perrinfo*<br/>
`IErrorInfo` オブジェクト。

*fAddRef*<br/>
既定値がコンス トラクターに null 以外の AddRef を呼び出すと、`IErrorInfo`インターフェイス。 これにより、正しい参照が、インターフェイスの所有権に渡される一般的なケースでカウント、 **_com_error**などオブジェクトします。

```cpp
throw _com_error(hr, perrinfo);
```

コード所有権の転送をしないかどうか、 **_com_error**オブジェクト、および`AddRef`をオフセットするために必要な`Release`で、 **_com_error**デストラクターとしてオブジェクトを構築次に示します。

```cpp
_com_error err(hr, perrinfo, true);
```

*それ*<br/>
既存の **_com_error**オブジェクト。

## <a name="remarks"></a>Remarks

最初のコンス トラクターは、HRESULT と省略可能な指定された新しいオブジェクトを作成します。`IErrorInfo`オブジェクト。 2 つ目は、既存のコピーを作成します。 **_com_error**オブジェクト。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_error クラス](../cpp/com-error-class.md)