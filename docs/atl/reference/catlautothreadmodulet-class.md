---
title: CAtlAutoThreadModuleT クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: 63f1c8dbe3c752773fd64c6e339a9a3b67051d35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247176"
---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT クラス

このクラスは、スレッド プール、アパートメント モデルの COM サーバーを実装するためのメソッドを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
COM サーバーを実装するクラスです。

*テンプレートパラ*<br/>
スレッドの選択を管理するクラスです。 既定値は[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)します。

*dwWait*<br/>
ミリ秒単位で、タイムアウト間隔を指定します。 既定値は、INFINITE で、決してメソッドのタイムアウト間隔が経過するとします。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|この静的関数は動的に計算し、プロセッサの数に基づいて、EXE モジュールのスレッドの最大数を返します。|

## <a name="remarks"></a>Remarks

クラスは、 [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)から派生した`CAtlAutoThreadModuleT`スレッド プール、アパートメント モデルの COM サーバーを実装するためにします。 古いクラスに置き換えられます[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)します。

> [!NOTE]
>  既定値として、DLL でこのクラスが使用されない必要があります*内部*無限の値、DLL が読み込まれるとデッドロックが発生します。

## <a name="inheritance-hierarchy"></a>継承階層

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="getdefaultthreads"></a>  CAtlAutoThreadModuleT::GetDefaultThreads

この静的関数は動的に計算し、プロセッサの数に基づいて、EXE モジュールのスレッドの最大数を返します。

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>戻り値

EXE モジュール内に作成するスレッドの数。

### <a name="remarks"></a>Remarks

スレッドの数を計算するための別の方法を使用する場合は、このメソッドをオーバーライドします。 既定では、スレッドの数がプロセッサの数に基づいています。

## <a name="see-also"></a>関連項目

[IAtlAutoThreadModule クラス](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[IAtlAutoThreadModule クラス](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[モジュール クラス](../../atl/atl-module-classes.md)
