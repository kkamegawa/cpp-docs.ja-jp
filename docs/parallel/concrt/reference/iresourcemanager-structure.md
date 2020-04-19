---
title: IResourceManager 構造体
ms.date: 03/27/2019
f1_keywords:
- IResourceManager
- CONCRTRM/concurrency::IResourceManager
- CONCRTRM/concurrency::IResourceManager::IResourceManager::OSVersion
- CONCRTRM/concurrency::IResourceManager::IResourceManager::CreateNodeTopology
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetAvailableNodeCount
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetFirstNode
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Reference
- CONCRTRM/concurrency::IResourceManager::IResourceManager::RegisterScheduler
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Release
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
ms.openlocfilehash: 7ce5b07f5eb4272db1b00b7f0105b790ddbb28fe
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142982"
---
# <a name="iresourcemanager-structure"></a>IResourceManager 構造体

コンカレンシー ランタイムのリソース マネージャーに対するインターフェイスです。 これは、スケジューラがリソース マネージャーと通信する際に使用されるインターフェイスです。

## <a name="syntax"></a>構文

```cpp
struct IResourceManager;
```

## <a name="members"></a>メンバー

### <a name="public-enumerations"></a>パブリック列挙体

|Name|説明|
|----------|-----------------|
|[IResourceManager:: OSVersion](#osversion)|オペレーティング システムのバージョンを表す列挙型。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[IResourceManager:: Creatモジュール Detopology](#createnodetopology)|このメソッドは、ランタイムのデバッグビルドにのみ存在します。この方法は、ハードウェアトポロジによって異なるリソースマネージャーのテストを容易にするために設計されたテストフックです。実際にハードウェアを構成する必要はありません。 ランタイムのリテールビルドでは、このメソッドは何もアクションを実行せずにを返します。|
|[IResourceManager:: GetAvailableNodeCount](#getavailablenodecount)|リソースマネージャーが使用できるノードの数を返します。|
|[IResourceManager:: GetFirstNode](#getfirstnode)|リソースマネージャーで定義されている列挙の順序で、最初のノードを返します。|
|[IResourceManager:: Reference](#reference)|リソースマネージャーインスタンスの参照カウントをインクリメントします。|
|[IResourceManager:: RegisterScheduler](#registerscheduler)|スケジューラをリソースマネージャーに登録します。 スケジューラが登録されると、返された `ISchedulerProxy` インターフェイスを使用して、リソースマネージャーと通信する必要があります。|
|[IResourceManager:: Release](#release)|Resource Manager インスタンスの参照カウントをデクリメントします。 リソースマネージャーは、参照カウントが `0`になると破棄されます。|

## <a name="remarks"></a>コメント

[Createresourcemanager](concurrency-namespace-functions.md)関数を使用して、シングルトンリソースマネージャーインスタンスへのインターフェイスを取得します。 メソッドは、リソースマネージャーの参照カウントをインクリメントします。 Resource Manager で終了したときに、 [Iresourcemanager:: release](#release)メソッドを呼び出して参照を解放する必要があります。 通常、作成する各スケジューラは、作成時にこのメソッドを呼び出し、シャットダウン後にリソースマネージャーへの参照を解放します。

## <a name="inheritance-hierarchy"></a>継承階層

`IResourceManager`

## <a name="requirements"></a>要件

**ヘッダー:** concrtrm. h

**名前空間:** concurrency

## <a name="createnodetopology"></a>IResourceManager:: Creatモジュール Detopology メソッド

このメソッドは、ランタイムのデバッグビルドにのみ存在します。この方法は、ハードウェアトポロジによって異なるリソースマネージャーのテストを容易にするために設計されたテストフックです。実際にハードウェアを構成する必要はありません。 ランタイムのリテールビルドでは、このメソッドは何もアクションを実行せずにを返します。

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>パラメーター

*nodeCount*<br/>
シミュレートされているプロセッサノードの数。

*pCoreCount*<br/>
各ノードのコア数を指定する配列。

*pNodeDistance*<br/>
2つのノード間のノード距離を指定する行列。 このパラメーターには `NULL`値を指定できます。

*pProcessorGroups*<br/>
各ノードが属するプロセッサグループを指定する配列。

### <a name="remarks"></a>コメント

パラメーター `nodeCount` に渡された `0` 値がある場合、またはパラメーター `pCoreCount` の値が `NULL`の場合は[invalid_argument](../../../standard-library/invalid-argument-class.md)がスローされます。

プロセスに他のスケジューラが存在する間にこのメソッドが呼び出されると、 [invalid_operation](invalid-operation-class.md)がスローされます。

## <a name="getavailablenodecount"></a>IResourceManager:: GetAvailableNodeCount メソッド

リソースマネージャーが使用できるノードの数を返します。

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>戻り値

リソースマネージャーが使用できるノードの数。

## <a name="getfirstnode"></a>IResourceManager:: GetFirstNode メソッド

リソースマネージャーで定義されている列挙の順序で、最初のノードを返します。

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>戻り値

リソースマネージャーによって定義された列挙順序の最初のノード。

## <a name="osversion"></a>IResourceManager:: OSVersion 列挙型

オペレーティング システムのバージョンを表す列挙型。

```cpp
enum OSVersion;
```

## <a name="reference"></a>IResourceManager:: Reference メソッド

リソースマネージャーインスタンスの参照カウントをインクリメントします。

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>戻り値

結果として得られる参照カウント。

## <a name="registerscheduler"></a>IResourceManager:: RegisterScheduler メソッド

スケジューラをリソースマネージャーに登録します。 スケジューラが登録されると、返された `ISchedulerProxy` インターフェイスを使用して、リソースマネージャーと通信する必要があります。

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>パラメーター

*pScheduler*<br/>
登録するスケジューラへの `IScheduler` インターフェイス。

*version*<br/>
スケジューラがリソースマネージャーとの通信に使用している通信インターフェイスのバージョン。 バージョンを使用すると、リソースマネージャーは通信インターフェイスを進化させながら、スケジューラが古い機能にアクセスできるようにすることができます。 Visual Studio 2010 に存在する Resource Manager 機能を使用するスケジューラは、バージョン `CONCRT_RM_VERSION_1`を使用する必要があります。

### <a name="return-value"></a>戻り値

リソースマネージャーによってスケジューラに関連付けられている `ISchedulerProxy` インターフェイス。 スケジューラは、このインターフェイスを使用して、この時点から Resource Manager と通信する必要があります。

### <a name="remarks"></a>コメント

このメソッドを使用して、リソースマネージャーとの通信を開始します。 メソッドは、スケジューラの `IScheduler` インターフェイスを `ISchedulerProxy` インターフェイスに関連付けて、ユーザーに送り返します。 返されたインターフェイスを使用して、スケジューラで使用するために実行リソースを要求したり、リソースマネージャーを使用してスレッドをサブスクライブしたりできます。 リソースマネージャーは、 [IScheduler:: GetPolicy](ischeduler-structure.md#getpolicy)メソッドによって返されるスケジューラポリシーのポリシー要素を使用して、スケジューラが作業を実行するために必要なスレッドの種類を決定します。 `SchedulerKind` ポリシーキーの値が `UmsThreadDefault` で、`UmsThreadDefault`値としてポリシーから値が読み取られている場合、メソッドに渡される `IScheduler` インターフェイスは `IUMSScheduler` インターフェイスである必要があります。

パラメーター `pScheduler` の値が `NULL` か、またはパラメーター `version` が通信インターフェイスの有効なバージョンではない場合、メソッドは `invalid_argument` 例外をスローします。

## <a name="release"></a>IResourceManager:: Release メソッド

Resource Manager インスタンスの参照カウントをデクリメントします。 リソースマネージャーは、参照カウントが `0`になると破棄されます。

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>戻り値

結果として得られる参照カウント。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[ISchedulerProxy 構造体](ischedulerproxy-structure.md)<br/>
[IScheduler 構造体](ischeduler-structure.md)
