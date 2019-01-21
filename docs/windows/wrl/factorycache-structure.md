---
title: FactoryCache 構造体
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
- module/Microsoft::WRL::Details::FactoryCache::cookie
- module/Microsoft::WRL::Details::FactoryCache::factory
helpviewer_keywords:
- Microsoft::WRL::Details::FactoryCache structure
- Microsoft::WRL::Details::FactoryCache::cookie data member
- Microsoft::WRL::Details::FactoryCache::factory data member
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
ms.openlocfilehash: 7196363567dffa43844bbbd1de76934a317302d1
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336741"
---
# <a name="factorycache-structure"></a>FactoryCache 構造体

Windows ランタイム C++ テンプレート ライブラリのインフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>Remarks

クラス ファクトリと、登録されている wrt を識別する値または COM クラスのオブジェクトの場所が含まれています。

## <a name="members"></a>メンバー

### <a name="public-data-members"></a>パブリック データ メンバー

名前                              | 説明
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[FactoryCache::cookie](#cookie)   | 登録済み Windows ランタイムまたは COM クラスのオブジェクトを識別し、オブジェクトの登録を解除する際に使用する値が含まれています。
[FactoryCache::factory](#factory) | Windows ランタイムまたは COM クラス ファクトリを指します。

## <a name="inheritance-hierarchy"></a>継承階層

`FactoryCache`

## <a name="requirements"></a>必要条件

**ヘッダー:** module.h

**名前空間:** Microsoft::WRL::Details

## <a name="cookie"></a>FactoryCache::cookie

Windows ランタイム C++ テンプレート ライブラリのインフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>Remarks

登録済み Windows ランタイムまたは COM クラスのオブジェクトを識別し、オブジェクトの登録を解除する際に使用する値が含まれています。

## <a name="factory"></a>FactoryCache::factory

Windows ランタイム C++ テンプレート ライブラリのインフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>Remarks

Windows ランタイムまたは COM クラス ファクトリを指します。
