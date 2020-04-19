---
title: DontUseNewUseMake クラス
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
ms.openlocfilehash: 02420f2657c7d7d6a7a0294f0321717a3bb2b5d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398538"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake クラス

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Remarks

演算子を使用できないように`new`で`RuntimeClass`します。 したがって、使用する必要があります、[関数](make-function.md)代わりにします。

## <a name="members"></a>メンバー

### <a name="public-operators"></a>パブリック演算子

名前                                             | 説明
------------------------------------------------ | ---------------------------------------------------------------------------
[Dontusenewusemake::operator 新しい](#operator-new) | 演算子をオーバー ロード`new`しで使用されていることを防ぎます`RuntimeClass`します。

## <a name="inheritance-hierarchy"></a>継承階層

`DontUseNewUseMake`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::WRL::Details

## <a name="operator-new"></a>Dontusenewusemake::operator 新しい

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>パラメーター

*__unnamed0*<br/>
割り当てるメモリのバイト数を指定する名前のないパラメーター。

*placement*<br/>
割り当てられる型。

### <a name="return-value"></a>戻り値

演算子をオーバー ロードする場合は、追加の引数を渡す方法を提供します`new`します。

### <a name="remarks"></a>Remarks

演算子をオーバー ロード`new`しで使用されていることを防ぎます`RuntimeClass`します。
