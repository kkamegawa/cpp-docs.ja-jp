---
title: IRelogger クラス
description: C++ビルドインサイト SDK IRelogger クラス参照。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0796cec3fe4ac6183279e8d8013a9550f18b61c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334074"
---
# <a name="irelogger-class"></a>IRelogger クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`IRelogger` クラスは、Windows イベントトレーシング (ETW) トレースを再ログ記録するためのインターフェイスを提供します。 これは、 [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md)関数と[MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md)関数で使用されます。 Relogger グループの一部として使用できる独自の relogger を作成するには、基本クラスとして `IRelogger` を使用します。

## <a name="syntax"></a>構文

```cpp
class IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
    virtual AnalysisControl OnBeginRelogging();
    virtual AnalysisControl OnEndRelogging();
    virtual AnalysisControl OnBeginReloggingPass();
    virtual AnalysisControl OnEndReloggingPass() ;

    virtual ~IRelogger();
};
```

## <a name="remarks"></a>解説

オーバーライドされていないすべての関数の既定の戻り値は `AnalysisControl::CONTINUE`です。 詳細については、「 [AnalysisControl](analysis-control-enum-class.md)」を参照してください。

## <a name="members"></a>メンバー

### <a name="destructor"></a>デストラクター

[~ IRelogger](#irelogger-destructor)

### <a name="functions"></a>関数

[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[Onsimpleevent](#on-simple-event)\
[Onstartactivity](#on-start-activity)\
[Onstopactivity](#on-stop-activity)\
[OnTraceInfo](#on-trace-info)

## <a name="irelogger-destructor"></a>~ IRelogger

IRelogger クラスを破棄します。

```cpp
virtual ~IRelogger();
```

## <a name="on-begin-relogging"></a>OnBeginRelogging

この関数は、再ログパスが開始される前に呼び出されます。

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

## <a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

この関数は、再ログパスの先頭で呼び出されます。

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

## <a name="on-end-relogging"></a>OnEndRelogging

この関数は、relogging パスが終了した後に呼び出されます。

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

## <a name="on-end-relogging-pass"></a>OnEndReloggingPass

この関数は、再ログパスの最後に呼び出されます。

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

## <a name="on-simple-event"></a>OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

この関数は、単純なイベントが処理されるときに呼び出されます。

### <a name="parameters"></a>パラメーター

*Eventstack*\
この単純なイベントのイベントスタック。 イベントスタックの詳細については、「 [Events](../event-table.md)」を参照してください。

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

## <a name="on-start-activity"></a>OnStartActivity

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

この関数は、アクティビティ開始イベントが処理されるときに呼び出されます。

### <a name="parameters"></a>パラメーター

*Eventstack*\
このアクティビティ開始イベントのイベントスタック。 イベントスタックの詳細については、「 [Events](../event-table.md)」を参照してください。

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

## <a name="on-stop-activity"></a>OnStopActivity

この関数は、アクティビティ停止イベントの処理中に呼び出されます。

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>パラメーター

*Eventstack*\
このアクティビティ停止イベントのイベントスタック。 イベントスタックの詳細については、「 [Events](../event-table.md)」を参照してください。

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

## <a name="on-trace-info"></a>OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

この関数は、すべての分析または再ログパスの開始時に1回呼び出されます。

### <a name="parameters"></a>パラメーター

*Traceinfo*\
使用されているトレースに関する有用なプロパティを格納している[Traceinfo](../cpp-event-data-types/trace-info.md)オブジェクト。

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

::: moniker-end
