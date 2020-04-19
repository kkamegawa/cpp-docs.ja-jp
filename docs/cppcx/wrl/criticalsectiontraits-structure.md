---
title: CriticalSectionTraits 構造体
ms.date: 09/26/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock method
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
ms.openlocfilehash: ce904ecbd9a5855c63fd43f07f88c215cef544ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398603"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits 構造体

専門、`CriticalSection`無効のクリティカル セクションまたはクリティカル セクションを解放する関数をサポートするオブジェクト。

## <a name="syntax"></a>構文

```
struct CriticalSectionTraits;
```

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

名前   | 説明
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | A`typedef`クリティカル セクションを指すポインターを定義します。 `Type` 見なさ`typedef CRITICAL_SECTION* Type;`します。

### <a name="public-methods"></a>パブリック メソッド

名前                                                       | 説明
---------------------------------------------------------- | -----------------
[CriticalSectionTraits::GetInvalidValue](#getinvalidvalue) | 専門、`CriticalSection`テンプレート、テンプレートが常に有効なされないようにします。
[Criticalsectiontraits::unlock](#unlock)                   | 専門、`CriticalSection`その it サポート、クリティカル セクションを指定したオブジェクトの所有権を解放するためのテンプレート。

## <a name="inheritance-hierarchy"></a>継承階層

`CriticalSectionTraits`

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>CriticalSectionTraits::GetInvalidValue

専門、`CriticalSection`テンプレート、テンプレートが常に有効なされないようにします。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>戻り値

常に無効な重要なセクションにポインターを返します。

### <a name="remarks"></a>Remarks

`Type`として修飾子が定義されている`typedef CRITICAL_SECTION* Type;`します。

## <a name="unlock"></a>Criticalsectiontraits::unlock

専門、`CriticalSection`その it サポート、クリティカル セクションを指定したオブジェクトの所有権を解放するためのテンプレート。

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>パラメーター

*cs*<br/>
クリティカル セクション オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

`Type`として修飾子が定義されている`typedef CRITICAL_SECTION* Type;`します。

詳細については、次を参照してください。**により関数**で、**同期関数**Windows API のドキュメントの「します。
