---
title: MixIn 構造体
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: 16fd6b46d616df7163a304afa7f32ac3c095d398
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325358"
---
# <a name="mixin-structure"></a>MixIn 構造体

ランタイム クラスが Windows ランタイム インターフェイス (存在する場合) から派生し、次にクラシック COM インターフェイスから派生していることを確認します。

## <a name="syntax"></a>構文

```cpp
template<
    typename Derived,
    typename MixInType,
    bool hasImplements = __is_base_of(Details::ImplementsBase, MixInType)
>
struct MixIn;
```

### <a name="parameters"></a>パラメーター

*派生*<br/>
派生した型、[実装](implements-structure.md)構造体。

*MixInType*<br/>
基本型。

*hasImplements*<br/>
**true**場合*MixInType*は現在の実装から派生した基本型です。**false**それ以外の場合。

## <a name="remarks"></a>Remarks

Windows ランタイムおよびクラスの COM インターフェイスの両方から派生したクラスは、クラスの宣言リストする必要があります最初に、Windows ランタイム インターフェイスを一覧表示し、し、すべてのクラシック COM のインターフェイスします。 **MixIn**により、インターフェイスが正しい順序で指定されているようになります。

## <a name="inheritance-hierarchy"></a>継承階層

`MixIn`

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[Microsoft::WRL 名前空間](microsoft-wrl-namespace.md)