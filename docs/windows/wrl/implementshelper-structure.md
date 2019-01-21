---
title: ImplementsHelper 構造体
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
- implements/Microsoft::WRL::Details::ImplementsHelper::IidCount
helpviewer_keywords:
- Microsoft::WRL::Details::ImplementsHelper structure
- Microsoft::WRL::Details::ImplementsHelper::CanCastTo method
- Microsoft::WRL::Details::ImplementsHelper::CastToUnknown method
- Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid method
- Microsoft::WRL::Details::ImplementsHelper::IidCount constant
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
ms.openlocfilehash: 250a59152e9b41eb48c453caaa696fdc8ca3d3b4
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336458"
---
# <a name="implementshelper-structure"></a>ImplementsHelper 構造体

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>パラメーター

*RuntimeClassFlagsT*<br/>
1 つまたは複数を指定するフラグのフィールド[RuntimeClassType](runtimeclasstype-enumeration.md)列挙子。

*ILst*<br/>
インターフェイスの Id の一覧。

*IsDelegateToClass*<br/>
指定**true**場合の現在のインスタンス`Implements`で最初のインターフェイス ID の基底クラスは、 *ILst*、それ以外の**false**。

## <a name="remarks"></a>Remarks

により、実装、[実装](implements-structure.md)構造体。

このテンプレートは、インターフェイスのリストを走査し、基本クラス、および有効にするために必要な情報として追加`QueryInterface`します。

## <a name="members"></a>メンバー

### <a name="protected-methods"></a>プロテクト メソッド

名前                                                    | 説明
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[Implementshelper::cancastto](#cancastto)               | 指定されたインターフェイス ID にポインターを取得します。
[Implementshelper::casttounknown](#casttounknown)       | 基になるポインターを取得します。 `IUnknown` 、現在のインターフェイス`Implements`構造体。
[ImplementsHelper::FillArrayWithIid](#fillarraywithiid) | 指定した配列の要素に現在の 0 番目のテンプレート パラメーターで指定されたインターフェイス ID を挿入します。
[ImplementsHelper::IidCount](#iidcount)                 | 現在の実装されたインターフェイス Id の数を保持`Implements`オブジェクト。

## <a name="inheritance-hierarchy"></a>継承階層

`ImplementsHelper`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::WRL::Details

## <a name="cancastto"></a>Implementshelper::cancastto

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);

HRESULT CanCastTo(
   _In_ const IID &iid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>パラメーター

*riid*<br/>
インターフェイス ID への参照

*ppv*<br/>
この操作が成功した場合、インターフェイスへのポインターが指定された*riid*または*iid*します。

*iid*<br/>
インターフェイス ID への参照

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

### <a name="remarks"></a>Remarks

指定されたインターフェイス ID にポインターを取得します。

## <a name="casttounknown"></a>Implementshelper::casttounknown

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>戻り値

基になるポインター`IUnknown`インターフェイス。

### <a name="remarks"></a>Remarks

基になるポインターを取得します。 `IUnknown` 、現在のインターフェイス`Implements`構造体。

## <a name="fillarraywithiid"></a>ImplementsHelper::FillArrayWithIid

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>パラメーター

*index*<br/>
この操作の開始の配列要素を示す 0 から始まるインデックス。 この操作が完了したら、*インデックス*1 ずつインクリメントされます。

*iid*<br/>
Iid 型の配列。

### <a name="remarks"></a>Remarks

指定した配列の要素に現在の 0 番目のテンプレート パラメーターで指定されたインターフェイス ID を挿入します。

## <a name="iidcount"></a>ImplementsHelper::IidCount

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Remarks

現在の実装されたインターフェイス Id の数を保持`Implements`オブジェクト。
