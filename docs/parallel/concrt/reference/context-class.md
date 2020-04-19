---
title: Context クラス
ms.date: 11/04/2016
f1_keywords:
- Context
- CONCRT/concurrency::Context
- CONCRT/concurrency::Context::Block
- CONCRT/concurrency::Context::CurrentContext
- CONCRT/concurrency::Context::GetId
- CONCRT/concurrency::Context::GetScheduleGroupId
- CONCRT/concurrency::Context::GetVirtualProcessorId
- CONCRT/concurrency::Context::Id
- CONCRT/concurrency::Context::IsCurrentTaskCollectionCanceling
- CONCRT/concurrency::Context::IsSynchronouslyBlocked
- CONCRT/concurrency::Context::Oversubscribe
- CONCRT/concurrency::Context::ScheduleGroupId
- CONCRT/concurrency::Context::Unblock
- CONCRT/concurrency::Context::VirtualProcessorId
- CONCRT/concurrency::Context::Yield
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
ms.openlocfilehash: 7c47d9db64b0af7d5413abed3f85e9d41a591fa2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143128"
---
# <a name="context-class"></a>Context クラス

実行コンテキストの抽象化を表します。

## <a name="syntax"></a>構文

```cpp
class Context;
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|Name|説明|
|----------|-----------------|
|[~ Context デストラクター](#dtor)||

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[ブロック](#block)|現在のコンテキストをブロックします。|
|[CurrentContext](#currentcontext)|現在のコンテキストへのポインターを返します。|
|[GetId](#getid)|コンテキストが属するスケジューラ内で一意のコンテキストの識別子を返します。|
|[GetScheduleGroupId](#getschedulegroupid)|コンテキストが現在実行されているスケジュール グループの識別子を返します。|
|[GetVirtualProcessorId](#getvirtualprocessorid)|コンテキストが現在実行されている仮想プロセッサの識別子を返します。|
|[Id](#id)|現在のコンテキストが属するスケジューラ内で一意の現在のコンテキストの識別子を返します。|
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|現在のコンテキストで現在インラインで実行されているタスク コレクションがアクティブなキャンセル処理中である (または間もなくキャンセル処理が開始される) かどうかを示す値を返します。|
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|コンテキストが同期的にブロックされているかどうかを判断します。 コンテキストがブロックを引き起こしたアクションを明示的に実行した場合、そのコンテキストは同期的にブロックされていると見なされます。|
|[オーバーサブスクライブ](#oversubscribe)|スケジューラの仮想プロセッサのいずれかで実行されるコンテキストで呼び出された場合に、コード ブロックの期間中、追加の仮想プロセッサをそのスケジューラに挿入します。|
|[ScheduleGroupId](#schedulegroupid)|現在のコンテキストが実行されているスケジュール グループの識別子を返します。|
|[解除](#unblock)|コンテキストのブロックを解除し、実行できるようにします。|
|[VirtualProcessorId](#virtualprocessorid)|現在のコンテキストが実行されている仮想プロセッサの識別子を返します。|
|[Yield](#yield)|別のコンテキストが実行できるように実行を譲歩します。 実行の権利を譲る他のコンテキストが存在しない場合、スケジューラによって別のオペレーティング システム スレッドに明け渡されます。|

## <a name="remarks"></a>コメント

同時実行ランタイム scheduler (「 [scheduler](scheduler-class.md)」を参照) は、実行コンテキストを使用して、アプリケーションによってキューに置かれた作業を実行します。 Win32 スレッドは、Windows オペレーティング システムの実行コンテキストの例です。

スケジューラのコンカレンシー レベルは、リソース マネージャーによって許可された仮想プロセッサの数と常に等しくなります。 仮想プロセッサとは、処理リソースを抽象化したものであり、基になるシステムのハードウェア スレッドに対応しています。 指定された時点に 1 つの仮想プロセッサで実行できるスケジューラ コンテキストは 1 つのみです。

スケジューラは本質的に協調的であるため、実行コンテキストが待機状態になると、常に仮想プロセッサを別のコンテキストに渡す可能性があります。 待機状態が終了すると、スケジューラの使用可能な仮想プロセッサが実行を開始するまで再開できません。

## <a name="inheritance-hierarchy"></a>継承階層

`Context`

## <a name="requirements"></a>要件

**ヘッダー:** concrt .h

**名前空間:** concurrency

## <a name="block"></a>帯

現在のコンテキストをブロックします。

```cpp
static void __cdecl Block();
```

### <a name="remarks"></a>コメント

呼び出し元のコンテキストにスケジューラが現在関連付けられていない場合、このメソッドを呼び出すと、プロセスの既定のスケジューラが作成されるか、または呼び出し元コンテキストにアタッチされます。

呼び出し元のコンテキストが仮想プロセッサ上で実行されている場合、仮想プロセッサは実行する別の実行可能なコンテキストを検出するか、新しいコンテキストを作成する可能性があります。

`Block` メソッドが呼び出された後、または呼び出された後に、もう一度実行するには、別の実行コンテキストから[ブロック解除](#unblock)メソッドを呼び出す必要があります。 コードが `Unblock` メソッドを呼び出すことができるようにするために、また、実際のメソッドの `Block` 呼び出しが行われる地点まで、コードが別のスレッドのコンテキストを公開するまでの間には重要な点があることに注意してください。 この期間中は、メソッドを呼び出さないでください。これらのメソッドは、独自の理由 (たとえば、ロックの取得) によってブロックおよびブロック解除することができます。 `Block` および `Unblock` メソッドの呼び出しでは、ブロックとブロック解除の理由は追跡されません。 1つのオブジェクトだけに `Unblock` ペアの `Block`- 所有権が必要です。

このメソッドは、 [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)を含むさまざまな例外をスローする場合があります。

## <a name="dtor"></a>~ コンテキスト

```cpp
virtual ~Context();
```

## <a name="currentcontext"></a>CurrentContext

現在のコンテキストへのポインターを返します。

```cpp
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>戻り値

現在のコンテキストへのポインター。

### <a name="remarks"></a>コメント

呼び出し元のコンテキストにスケジューラが現在関連付けられていない場合、このメソッドを呼び出すと、プロセスの既定のスケジューラが作成されるか、または呼び出し元コンテキストにアタッチされます。

## <a name="getid"></a>GetId

コンテキストが属するスケジューラ内で一意のコンテキストの識別子を返します。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>戻り値

コンテキストが属するスケジューラ内で一意のコンテキストの識別子。

## <a name="getschedulegroupid"></a>GetScheduleGroupId

コンテキストが現在実行されているスケジュール グループの識別子を返します。

```cpp
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>戻り値

コンテキストが現在処理されているスケジュールグループの識別子。

### <a name="remarks"></a>コメント

このメソッドからの戻り値は、コンテキストが実行されているスケジュールグループの瞬間的なサンプリングです。 現在のコンテキスト以外のコンテキストでこのメソッドが呼び出された場合、値は返された時点で古くなる可能性があり、依存することはできません。 通常、このメソッドは、デバッグまたはトレースの目的でのみ使用されます。

## <a name="getvirtualprocessorid"></a>GetVirtualProcessorId

コンテキストが現在実行されている仮想プロセッサの識別子を返します。

```cpp
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>戻り値

コンテキストが現在仮想プロセッサで実行されている場合は、コンテキストが現在実行されている仮想プロセッサの識別子。それ以外の場合は、`-1`値です。

### <a name="remarks"></a>コメント

このメソッドからの戻り値は、コンテキストが実行されている仮想プロセッサの瞬間的なサンプリングです。 この値は、返される瞬間に古くなる可能性があり、依存することはできません。 通常、このメソッドは、デバッグまたはトレースの目的でのみ使用されます。

## <a name="id"></a>番号

現在のコンテキストが属するスケジューラ内で一意の現在のコンテキストの識別子を返します。

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>戻り値

現在のコンテキストがスケジューラにアタッチされている場合、現在のコンテキストが属するスケジューラ内で一意の現在のコンテキストの識別子。それ以外の場合は、`-1`値です。

## <a name="iscurrenttaskcollectioncanceling"></a>IsCurrentTaskCollectionCanceling

現在のコンテキストで現在インラインで実行されているタスク コレクションがアクティブなキャンセル処理中である (または間もなくキャンセル処理が開始される) かどうかを示す値を返します。

```cpp
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>戻り値

スケジューラが呼び出し元のコンテキストにアタッチされていて、タスクグループがそのコンテキストでインラインタスクを実行している場合、そのタスクグループがアクティブなキャンセル処理中であるかどうかを示します (または、間もなく有効になります)。それ以外の場合は、`false`値です。

## <a name="issynchronouslyblocked"></a>IsSynchronouslyBlocked

コンテキストが同期的にブロックされているかどうかを判断します。 コンテキストがブロックを引き起こしたアクションを明示的に実行した場合、そのコンテキストは同期的にブロックされていると見なされます。

```cpp
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>戻り値

コンテキストが同期的にブロックされているかどうか。

### <a name="remarks"></a>コメント

コンテキストがブロックを引き起こしたアクションを明示的に実行した場合、そのコンテキストは同期的にブロックされていると見なされます。 スレッドスケジューラでは、これは、`Context::Block` メソッドまたは `Context::Block` メソッドを使用して構築された同期オブジェクトへの直接呼び出しを示します。

このメソッドからの戻り値は、コンテキストが同期的にブロックされているかどうかを示す瞬時のサンプルです。 この値は、返される瞬間に古くなる可能性があり、非常に限定的な状況でのみ使用できます。

## <a name="operator_delete"></a>delete 演算子

`Context` オブジェクトは、ランタイムによって内部的に破棄されます。 明示的に削除することはできません。

```cpp
void operator delete(void* _PObject);
```

### <a name="parameters"></a>パラメーター

*_PObject*<br/>
削除するオブジェクトへのポインター。

## <a name="oversubscribe"></a>オーバーサブスクライブ

スケジューラの仮想プロセッサのいずれかで実行されるコンテキストで呼び出された場合に、コード ブロックの期間中、追加の仮想プロセッサをそのスケジューラに挿入します。

```cpp
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>パラメーター

*_BeginOversubscription*<br/>
**True**の場合は、オーバーサブスクリプションの間に追加の仮想プロセッサを追加する必要があることを示します。 **False**の場合は、オーバーサブスクリプションを終了し、以前に追加した仮想プロセッサを削除する必要があることを示します。

## <a name="schedulegroupid"></a>ScheduleGroupId

現在のコンテキストが実行されているスケジュール グループの識別子を返します。

```cpp
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>戻り値

現在のコンテキストがスケジューラにアタッチされ、スケジュールグループで作業している場合は、現在のコンテキストが動作しているスケジューラグループの識別子。それ以外の場合は、`-1`値です。

## <a name="unblock"></a>解除

コンテキストのブロックを解除し、実行できるようにします。

```cpp
virtual void Unblock() = 0;
```

### <a name="remarks"></a>コメント

`Unblock` メソッドの呼び出しが、[ブロック](#block)メソッドへの対応する呼び出しの前に来るようにすることは、完全に有効です。 `Block` メソッドと `Unblock` メソッドの呼び出しが適切にペアになっている限り、ランタイムはどちらの順序の自然な競合を適切に処理します。 `Block` 呼び出しの前に `Unblock` 呼び出しを行うと、`Block` 呼び出しの効果が単に否定されます。

このメソッドからスローされる可能性がある例外がいくつかあります。 コンテキストがそれ自体で `Unblock` メソッドを呼び出そうとすると、 [context_self_unblock](context-self-unblock-class.md)例外がスローされます。 `Block` と `Unblock` の呼び出しが適切にペアになっていない場合 (たとえば、現在実行されているコンテキストに対して `Unblock` の2回の呼び出しが行われた場合)、 [context_unblock_unbalanced](context-unblock-unbalanced-class.md)例外がスローされます。

コードが `Unblock` メソッドを呼び出すことができるようにするために、また、実際のメソッドの `Block` 呼び出しが行われる地点まで、コードが別のスレッドのコンテキストを公開するまでの間には重要な点があることに注意してください。 この期間中は、メソッドを呼び出さないでください。これらのメソッドは、独自の理由 (たとえば、ロックの取得) によってブロックおよびブロック解除することができます。 `Block` および `Unblock` メソッドの呼び出しでは、ブロックとブロック解除の理由は追跡されません。 `Block` と `Unblock` ペアの所有権を持つことができるオブジェクトは1つだけです。

## <a name="virtualprocessorid"></a>VirtualProcessorId

現在のコンテキストが実行されている仮想プロセッサの識別子を返します。

```cpp
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>戻り値

現在のコンテキストがスケジューラにアタッチされている場合は、現在のコンテキストが実行されている仮想プロセッサの識別子。それ以外の場合は、`-1`値です。

### <a name="remarks"></a>コメント

このメソッドからの戻り値は、現在のコンテキストが実行されている仮想プロセッサの瞬間的なサンプリングです。 この値は、返される瞬間に古くなる可能性があり、依存することはできません。 通常、このメソッドは、デバッグまたはトレースの目的でのみ使用されます。

## <a name="yield"></a>得

別のコンテキストが実行できるように実行を譲歩します。 実行の権利を譲る他のコンテキストが存在しない場合、スケジューラによって別のオペレーティング システム スレッドに明け渡されます。

```cpp
static void __cdecl Yield();
```

### <a name="remarks"></a>コメント

呼び出し元のコンテキストにスケジューラが現在関連付けられていない場合、このメソッドを呼び出すと、プロセスの既定のスケジューラが作成されるか、または呼び出し元コンテキストにアタッチされます。

## <a name="yieldexecution"></a>YieldExecution

別のコンテキストが実行できるように実行を譲歩します。 実行の権利を譲る他のコンテキストが存在しない場合、スケジューラによって別のオペレーティング システム スレッドに明け渡されます。

```cpp
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>コメント

呼び出し元のコンテキストにスケジューラが現在関連付けられていない場合、このメソッドを呼び出すと、プロセスの既定のスケジューラが作成されるか、または呼び出し元コンテキストにアタッチされます。

この関数は Visual Studio 2015 で新しく追加されたものであり、 [yield](#yield)関数と同じですが、Windows .H の yield マクロと競合しません。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[Scheduler クラス](scheduler-class.md)<br/>
[タスク スケジューラ](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
