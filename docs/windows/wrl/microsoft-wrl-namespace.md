---
title: Microsoft::WRL 名前空間
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL
- module/Microsoft::WRL
- async/Microsoft::WRL
- internal/Microsoft::WRL
- event/Microsoft::WRL
- ftm/Microsoft::WRL
- client/Microsoft::WRL
- corewrappers/Microsoft::WRL
helpviewer_keywords:
- WRL namespace
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
ms.openlocfilehash: d402f2a1292088b52ce921bbc0007ab96554189e
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336822"
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL 名前空間

Windows ランタイム C++ テンプレート ライブラリを構成する基本的な型を定義します。

## <a name="syntax"></a>構文

```cpp
namespace Microsoft::WRL;
```

## <a name="members"></a>メンバー

### <a name="typedefs"></a>Typedef

|名前|説明|
|----------|-----------------|
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt | InhibitWeakReference >'|

### <a name="classes"></a>クラス

|名前|説明|
|----------|-----------------|
|[ActivationFactory クラス](activationfactory-class.md)|1 つ以上のクラスを Windows ランタイムによってアクティブ化できるようにします。|
|[AsyncBase クラス](asyncbase-class.md)|Windows ランタイムの非同期ステート マシンを実装します。|
|[ClassFactory クラス](classfactory-class.md)|`IClassFactory` インターフェイスの基本機能を実装します。|
|[ComPtr クラス](comptr-class.md)|テンプレート パラメーターで指定されたインターフェイスを表す *スマート ポインター* 型を作成します。 ComPtr は、基になるインターフェイス ポインターの参照カウントを自動的に維持し、参照カウントがゼロになるとそのインターフェイスを解放します。|
|[DeferrableEventArgs クラス](deferrableeventargs-class.md)|遅延のイベント引数の型に使用されるテンプレート クラス。|
|[EventSource クラス](eventsource-class.md)|イベントを表します。 `EventSource` メンバー関数は、イベント ハンドラーの追加、削除、および呼び出しを実行します。|
|[FtmBase クラス](ftmbase-class.md)|フリー スレッド マーシャラー オブジェクトを表します。|
|[Module クラス](module-class.md)|関連するオブジェクトから成るコレクションを表します。|
|[RuntimeClass クラス](runtimeclass-class.md)|指定した数のインターフェイスを継承し、指定した Windows ランタイム、クラシック COM、および弱い参照をサポートする、インスタンス化されたクラスを表します。|
|[SimpleActivationFactory クラス](simpleactivationfactory-class.md)|Windows ランタイムまたはクラシック COM の基底クラスを作成するための基本的なメカニズムを提供します。|
|[SimpleClassFactory クラス](simpleclassfactory-class.md)|基底クラスを作成するための基本的なメカニズムを提供します。|
|[WeakRef クラス](weakref-class.md)|クラシック COM ではなく、Windows ランタイムでのみ使用できる *弱い参照* を表します。 弱い参照は、アクセスできる場合とできない場合があるオブジェクトを表します。|

### <a name="structures"></a>構造体

|名前|説明|
|----------|-----------------|
|[ChainInterfaces 構造体](chaininterfaces-structure.md)|一連のインターフェイス ID に適用できる検証および初期化関数を指定します。|
|[CloakedIid 構造体](cloakediid-structure.md)|示します、 `RuntimeClass`、`Implements`と`ChainInterfaces`テンプレートの指定したインターフェイスが IID リストにアクセスできないことです。|
|[Implements 構造体](implements-structure.md)|実装`QueryInterface`と`GetIid`のインターフェイスで指定します。|
|[MixIn 構造体](mixin-structure.md)|ランタイム クラスが Windows ランタイム インターフェイス (存在する場合) から派生し、次にクラシック COM インターフェイスから派生していることを確認します。|
|[RuntimeClassFlags 構造体](runtimeclassflags-structure.md)|インスタンスの型が含まれています、 [RuntimeClass](runtimeclass-class.md)します。|

### <a name="enumerations"></a>列挙

|名前|説明|
|----------|-----------------|
|[AsyncResultType 列挙型](asyncresulttype-enumeration.md)|によって返される結果の種類を指定します、`GetResults()`メソッド。|
|[ModuleType 列挙型](moduletype-enumeration.md)|モジュールがインプロセス サーバーまたはアウトプロセス サーバーをサポートするかどうかを指定します。|
|[RuntimeClassType 列挙型](runtimeclasstype-enumeration.md)|型を指定[RuntimeClass](runtimeclass-class.md)サポートされているインスタンス。|

### <a name="functions"></a>関数

|名前|説明|
|----------|-----------------|
|[AsWeak 関数](asweak-function.md)|指定されたインスタンスへの弱い参照を取得します。|
|[Callback 関数 (WRL)](callback-function-wrl.md)|メンバー関数がコールバック メソッドであるオブジェクトを作成します。|
|[CreateActivationFactory 関数](createactivationfactory-function.md)|Windows ランタイムによるアクティブ化が可能な、指定されたクラスのインスタンスを生成するファクトリを作成します。|
|[CreateClassFactory 関数](createclassfactory-function.md)|指定されたクラスのインスタンスを生成するファクトリを作成します。|
|[Make 関数](make-function.md)|指定した Windows ランタイム クラスを初期化します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** async.h、client.h、corewrappers.h、event.h、ftm.h、implements.h、internal.h、module.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[Microsoft::WRL::Wrappers 名前空間](microsoft-wrl-wrappers-namespace.md)