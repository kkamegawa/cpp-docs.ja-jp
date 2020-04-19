---
title: ActivatableClass マクロ
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
ms.openlocfilehash: 7d38db9e7d3fa94c89195b6379e14692f26f7ee5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62304138"
---
# <a name="activatableclass-macros"></a>ActivatableClass マクロ

指定したクラスのインスタンスを作成できるファクトリを含む内部キャッシュを設定します。

## <a name="syntax"></a>構文

```cpp
ActivatableClass(
   className
);

ActivatableClassWithFactory(
   className,
   factory
);

ActivatableClassWithFactoryEx(
   className,
   factory,
   serverName
);
```

### <a name="parameters"></a>パラメーター

*className*<br/>
作成するクラスの名前です。

*ファクトリ*<br/>
指定したクラスのインスタンスを作成するファクトリ。

*serverName*<br/>
モジュールのファクトリのサブセットを指定する名前。

## <a name="remarks"></a>Remarks

これらのマクロで使わないクラシック COM を使用しない限り、`#undef`ことを確認するディレクティブ、`__WRL_WINRT_STRICT__`マクロ定義が削除されます。

## <a name="requirements"></a>必要条件

**ヘッダー:** module.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[Module クラス](module-class.md)