---
title: IAnalyzer クラス
description: C++ビルドインサイト SDK ianalyzer クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 53f7b36695bb24d96ccfe88afbb56ff717c94dc9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334080"
---
# <a name="ianalyzer-class"></a>IAnalyzer クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`IAnalyzer` クラスは、Windows イベントトレーシング (ETW) トレースを分析するためのインターフェイスを提供します。 これは、 [MakeDynamicAnalyzerGroup](../functions/make-dynamic-analyzer-group.md)、 [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md)、 [MakeStaticAnalyzerGroup](../functions/make-dynamic-analyzer-group.md)、 [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md)の各関数で使用されます。 Analyzer または relogger グループの一部として使用できる独自のアナライザーを作成するには、基本クラスとして `IAnalyzer` を使用します。

## <a name="syntax"></a>構文

```cpp
class IAnalyzer : public IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
    virtual AnalysisControl OnStopActivity(const EventStack& eventStack)
    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
    virtual AnalysisControl OnBeginAnalysis();
    virtual AnalysisControl OnEndAnalysis();
    virtual AnalysisControl OnBeginAnalysisPass();
    virtual AnalysisControl OnEndAnalysisPass();

    AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnBeginRelogging() final;
    AnalysisControl OnEndRelogging() final;
    AnalysisControl OnBeginReloggingPass() final;
    AnalysisControl OnEndReloggingPass() final;

    virtual ~IAnalyzer();
};
```

## <a name="remarks"></a>解説

`IAnalyzer` から派生したクラスは、アナライザーと reloggers の両方として使用できます。 Reloggers として使用すると、reloggers 固有の関数は、同等のアナライザーにリダイレクトされます。 逆は true ではありません。 `IRelogger` から派生したクラスをアナライザーとして使用することはできません。 Relogger グループでアナライザーを使用するのは、一般的なパターンです。 Analyzer は、relogger グループの初期位置に配置された場合、情報を事前に計算し、後で再ロガーに使用できるようにすることができます。

オーバーライドされていないすべての関数の既定の戻り値は `AnalysisControl::CONTINUE`です。 詳細については、「 [AnalysisControl](analysis-control-enum-class.md)」を参照してください。

## <a name="members"></a>メンバー

`IRelogger` インターフェイスの[Ontraceinfo](irelogger-class.md#on-trace-info)メンバーに加えて、`IAnalyzer` クラスには次のメンバーが含まれています。

### <a name="destructor"></a>デストラクター

[~ IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>関数

[OnBeginAnalysis](#on-begin-analysis)\
[OnBeginAnalysisPass](#on-begin-analysis-pass)\
[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndAnalysis](#on-end-analysis)\
[OnEndAnalysisPass](#on-end-analysis-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[Onsimpleevent](#on-simple-event)\
[Onstartactivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)

## <a name="ianalyzer-destructor"></a>~ IAnalyzer

IAnalyzer クラスを破棄します。

```cpp
virtual ~IAnalyzer();
```

## <a name="on-begin-analysis"></a>OnBeginAnalysis

Analyzer グループのアナライザーの一部では、最初の分析パスが開始される前に、この関数が呼び出されます。 アナライザーが relogger グループの一部である場合、この関数は、再ログパスが開始される前に呼び出されます。 同じ再ログセッションのアナライザーと relogger グループの両方に含まれるアナライザーの場合、この関数は最初の分析パスが開始される前に2回呼び出されます。

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

## <a name="on-begin-analysis-pass"></a>OnBeginAnalysisPass

アナライザーグループの一部のアナライザーでは、この関数はすべての分析パスの先頭で呼び出されます。 アナライザーが relogger グループの一部である場合、この関数は relogger パスの先頭で呼び出されます。 同じ再ログセッションのアナライザーと relogger グループの両方に含まれるアナライザーの場合、この関数は、すべての分析パスの先頭と、relogger パスの先頭で呼び出されます。

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

## <a name="on-begin-relogging"></a>OnBeginRelogging

```cpp
AnalysisControl OnBeginRelogging() final;
```

この関数をオーバーライドすることはできません。 Analyzer が relogger グループC++の一部である場合、これは BUILD Insights SDK によって呼び出されます。 この関数は、 [OnBeginAnalysis](#on-begin-analysis)への呼び出しをリダイレクトします。

### <a name="return-value"></a>戻り値

[OnBeginAnalysis](#on-begin-analysis)呼び出しの結果。

## <a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

この関数をオーバーライドすることはできません。 Analyzer が relogger グループC++の一部である場合、これは BUILD Insights SDK によって呼び出されます。 この関数は、 [OnBeginAnalysisPass](#on-begin-analysis-pass)への呼び出しをリダイレクトします。

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>戻り値

[OnBeginAnalysisPass](#on-begin-analysis-pass)呼び出しの結果。

## <a name="on-end-analysis"></a>OnEndAnalysis

アナライザーグループに含まれるアナライザーの場合、この関数は最後の分析パスが終了した後に呼び出されます。 Relogger グループに含まれるアナライザーの場合、この関数は、再ログパスが終了した後に呼び出されます。 同じ再ログセッションのアナライザーと relogger グループの両方に含まれるアナライザーの場合、この関数は2回呼び出されます。

1. すべての分析が終了した後、再ログパスが開始される前に、
1. 再ログパスが終了した後。

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

## <a name="on-end-analysis-pass"></a>OnEndAnalysisPass

アナライザーグループの一部のアナライザーでは、この関数はすべての分析パスの最後に呼び出されます。 アナライザーが relogger グループの一部である場合、この関数は relogger パスの最後に呼び出されます。 同じ再ログセッションのアナライザーと relogger グループの両方に含まれるアナライザーの場合、この関数は、すべての分析パスの最後と、relogger パスの最後に呼び出されます。

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

## <a name="on-end-relogging"></a>OnEndRelogging

この関数をオーバーライドすることはできません。 Analyzer が relogger グループC++の一部である場合、これは BUILD Insights SDK によって呼び出されます。 この関数は、 [OnEndAnalysis](#on-end-analysis)への呼び出しをリダイレクトします。

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>戻り値

[OnEndAnalysis](#on-end-analysis)呼び出しの結果。

## <a name="on-end-relogging-pass"></a>OnEndReloggingPass

この関数をオーバーライドすることはできません。 Analyzer が relogger グループC++の一部である場合、これは BUILD Insights SDK によって呼び出されます。 この関数は、 [OnEndAnalysisPass](#on-end-analysis-pass)への呼び出しをリダイレクトします。

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>戻り値

[OnEndAnalysisPass](#on-end-analysis-pass)呼び出しの結果。

## <a name="on-simple-event"></a>OnSimpleEvent

この関数は、単純なイベントが処理されるときに呼び出されます。 この関数の2番目のバージョンをオーバーライドすることはできません。 Analyzer が relogger グループC++の一部である場合、これは BUILD Insights SDK によって呼び出されます。 バージョン2へのすべての呼び出しは、バージョン1にリダイレクトされます。

### <a name="version-1"></a>Version 1

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

### <a name="version-2"></a>Version 2

```cpp
AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>パラメーター

*Eventstack*\
この単純なイベントのイベントスタック。 イベントスタックの詳細については、「 [Events](../event-table.md)」を参照してください。

*Relogsession*\
このパラメーターは使用されません。

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

## <a name="on-start-activity"></a>OnStartActivity

この関数は、アクティビティ開始イベントが処理されるときに呼び出されます。 この関数の2番目のバージョンをオーバーライドすることはできません。 Analyzer が relogger グループC++の一部である場合、これは BUILD Insights SDK によって呼び出されます。 バージョン2へのすべての呼び出しは、バージョン1にリダイレクトされます。

### <a name="version-1"></a>Version 1

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>Version 2

```cpp
AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>パラメーター

*Eventstack*\
このアクティビティ開始イベントのイベントスタック。 イベントスタックの詳細については、「 [Events](../event-table.md)」を参照してください。

*Relogsession*\
このパラメーターは使用されません。

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

## <a name="on-stop-activity"></a>OnStopActivity

この関数は、アクティビティ停止イベントの処理中に呼び出されます。 この関数の2番目のバージョンをオーバーライドすることはできません。 Analyzer が relogger グループC++の一部である場合、これは BUILD Insights SDK によって呼び出されます。 バージョン2へのすべての呼び出しは、バージョン1にリダイレクトされます。

### <a name="version-1"></a>Version 1

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>Version 2

```cpp
AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>パラメーター

*Eventstack*\
このアクティビティ停止イベントのイベントスタック。 イベントスタックの詳細については、「 [Events](../event-table.md)」を参照してください。

*Relogsession*\
このパラメーターは使用されません。

### <a name="return-value"></a>戻り値

次に何が行われるかを説明する[AnalysisControl](analysis-control-enum-class.md)コード。

::: moniker-end
