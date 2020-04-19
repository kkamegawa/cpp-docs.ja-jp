---
title: VerifyInheritanceHelper 構造体
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInheritanceHelper structure
- Microsoft::WRL::Details::VerifyInheritanceHelper::Verify method
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
ms.openlocfilehash: c37a0eb74fd65b3d349d5b8b7c792fbaf7d1ac9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398083"
---
# <a name="verifyinheritancehelper-structure"></a>VerifyInheritanceHelper 構造体

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template <typename I, typename Base>
struct VerifyInheritanceHelper;

template <typename I>
struct VerifyInheritanceHelper<I, Nil>;
```

### <a name="parameters"></a>パラメーター

*I*<br/>
型。

*ベース*<br/>
別の型。

## <a name="remarks"></a>Remarks

1 つのインターフェイスが別のインターフェイスから派生したかどうかをテストします。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

名前                                       | 説明
------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------
[Verifyinheritancehelper::verify](#verify) | 現在のテンプレート パラメーターで指定された 2 つのインターフェイスをテストし、1 つのインターフェイスは、その他から派生されているかどうかを決定します。

## <a name="inheritance-hierarchy"></a>継承階層

`VerifyInheritanceHelper`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::WRL::Details

## <a name="verify"></a>Verifyinheritancehelper::verify

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
static void Verify();
```

### <a name="remarks"></a>Remarks

現在のテンプレート パラメーターで指定された 2 つのインターフェイスをテストし、1 つのインターフェイスは、その他から派生されているかどうかを決定します。

1 つのインターフェイスは、その他から派生していない場合は、エラーが生成されます。
