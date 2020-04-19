---
title: SyncLockWithStatusT クラス
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT class
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT, constructor
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
ms.openlocfilehash: 1c9c0805834a59d10a559bfc2b6da0f10e2fe160
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398135"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT クラス

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>パラメーター

*SyncTraits*<br/>
排他的に使用できる型またはリソースの所有権を共有します。

## <a name="remarks"></a>Remarks

排他的に使用できる型を表すか、リソースの所有権を共有します。

`SyncLockWithStatusT`クラスが実装するために使用される、[ミュー テックス](mutex-class.md)と[セマフォ](semaphore-class.md)クラス。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                                             | 説明
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | `SyncLockWithStatusT` クラスの新しいインスタンスを初期化します。

### <a name="protected-constructors"></a>プロテクト コンストラクター

名前                                                             | 説明
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT::SyncLockWithStatusT](#synclockwithstatust) | `SyncLockWithStatusT` クラスの新しいインスタンスを初期化します。

### <a name="public-methods"></a>パブリック メソッド

名前                                         | 説明
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::GetStatus](#getstatus) | 現在の待機状態を取得`SyncLockWithStatusT`オブジェクト。
[SyncLockWithStatusT::IsLocked](#islocked)   | 示すかどうか、現在`SyncLockWithStatusT`リソースを所有するオブジェクトです。 つまり、`SyncLockWithStatusT`オブジェクトが*ロック*します。

### <a name="protected-data-members"></a>プロテクト データ メンバー

名前                                    | 説明
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT::status_](#status) | 基になる待機操作の結果を保持するオブジェクトのロック操作が現在に基づいて後`SyncLockWithStatusT`オブジェクト。

## <a name="inheritance-hierarchy"></a>継承階層

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers::Details

## <a name="getstatus"></a>SyncLockWithStatusT::GetStatus

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>戻り値

基づくオブジェクトの待機操作の結果、`SyncLockWithStatusT`クラスなど、[ミュー テックス](mutex-class.md)または[セマフォ](semaphore-class.md)します。 ゼロ (0) では、待機操作にはシグナルの状態が返されることを示しますそれ以外の場合、別の状態が発生しました、タイムアウト値が経過した場合など。

### <a name="remarks"></a>Remarks

現在の待機状態を取得`SyncLockWithStatusT`オブジェクト。

GetStatus() 関数は、基になる値を取得[status _](#status)データ メンバー。 基づくオブジェクト、`SyncLockWithStatusT`クラスは、ロック操作を実行、使用可能になるオブジェクトのオブジェクトが最初に待機します。 待機操作の結果は、`status_`データ メンバー。 可能な値、`status_`データ メンバーは、待機操作の戻り値。 詳細については、の戻り値を参照してください、 `WaitForSingleObjectEx()` MSDN ライブラリ内の関数。

## <a name="islocked"></a>SyncLockWithStatusT::IsLocked

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>Remarks

示すかどうか、現在`SyncLockWithStatusT`リソースを所有するオブジェクトです。 つまり、`SyncLockWithStatusT`オブジェクトが*ロック*します。

### <a name="return-value"></a>戻り値

**true**場合、`SyncLockWithStatusT`オブジェクトがロックされている場合はそれ以外の場合、 **false**します。

## <a name="status"></a>SyncLockWithStatusT::status_

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
DWORD status_;
```

### <a name="remarks"></a>Remarks

基になる待機操作の結果を保持するオブジェクトのロック操作が現在に基づいて後`SyncLockWithStatusT`オブジェクト。

## <a name="synclockwithstatust"></a>SyncLockWithStatusT::SyncLockWithStatusT

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
SyncLockWithStatusT(
   _Inout_ SyncLockWithStatusT&& other
);

explicit SyncLockWithStatusT(
   typename SyncTraits::Type sync,
   DWORD status
);
```

### <a name="parameters"></a>パラメーター

*other*<br/>
別の右辺値参照`SyncLockWithStatusT`オブジェクト。

*sync*<br/>
別の参照`SyncLockWithStatusT`オブジェクト。

*status*<br/>
値、 [status _](#status)のデータ メンバー、*他*パラメーターまたは*同期*パラメーター。

### <a name="remarks"></a>Remarks

`SyncLockWithStatusT` クラスの新しいインスタンスを初期化します。

最初のコンス トラクターは、現在`SyncLockWithStatusT`から別のオブジェクト`SyncLockWithStatusT`パラメーターで指定された*他*、し、もう一方を無効に`SyncLockWithStatusT`オブジェクト。 2 番目のコンス トラクターは`protected`、し、現在初期化`SyncLockWithStatusT`オブジェクトを無効な状態にします。
