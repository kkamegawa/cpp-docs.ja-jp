---
title: VerifyInterfaceHelper 構造体
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
ms.openlocfilehash: cdd0272953b2399cd71efe207eb1c56e5de154e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398096"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper 構造体

Windows ランタイム C++ テンプレート ライブラリのインフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template <bool isWinRTInterface, typename I>
struct VerifyInterfaceHelper;

template <typename I>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>パラメーター

*I*<br/>
インターフェイスを確認します。

*isWinRTInterface*

## <a name="remarks"></a>Remarks

テンプレート パラメーターで指定されたインターフェイスが特定の要件を満たしていることを確認します。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

名前                                            | 説明
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify メソッド](#verify) | 現在のテンプレート パラメーターで指定されたインターフェイスが特定の要件を満たしていることを確認します。

## <a name="inheritance-hierarchy"></a>継承階層

`VerifyInterfaceHelper`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::WRL::Details

## <a name="verify"></a>Verifyinterfacehelper::verify

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
static void Verify();
```

### <a name="remarks"></a>Remarks

現在のテンプレート パラメーターで指定されたインターフェイスが特定の要件を満たしていることを確認します。
