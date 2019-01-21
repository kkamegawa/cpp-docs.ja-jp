---
title: IsBaseOfStrict 構造体
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
ms.openlocfilehash: 85aeb71ceaa162cc6366836dd286f2f9983d34e2
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336818"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict 構造体

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>パラメーター

*ベース*<br/>
基本データ型。

*派生*<br/>
派生型。

## <a name="remarks"></a>Remarks

一方の型がもう一方の型の基本クラスであるかどうかをテストします。

最初のテンプレートが生じる場合の基本型から派生する型かどうかをテストする**true**または**false**します。 2 番目のテンプレートはから派生した型自体には、常に生成するかどうかをテストする**false**します。

## <a name="members"></a>メンバー

### <a name="public-constants"></a>パブリック定数

名前                            | 説明
------------------------------- | --------------------------------------------------
[IsBaseOfStrict::value](#value) | 1 つの型が別のベースであるかどうかを示します。

## <a name="inheritance-hierarchy"></a>継承階層

`IsBaseOfStrict`

## <a name="requirements"></a>必要条件

**ヘッダー:** internal.h

**名前空間:** Microsoft::WRL::Details

## <a name="value"></a>IsBaseOfStrict::value

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>Remarks

1 つの型が別のベースであるかどうかを示します。

`value` **true**場合型`Base`型の基本クラスは、 `Derived`、それ以外の場合は**false**します。
