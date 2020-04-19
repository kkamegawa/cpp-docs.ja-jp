---
title: C++Build Insights SDK
description: Visual Studio C++ BUILD Insights SDK の概要です。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5aafcc65bc30de77131d1945c9f4e78361db14ed
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334032"
---
# <a name="c-build-insights-sdk"></a>C++Build Insights SDK

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

C++ BUILD insights SDK は、 C++ビルドインサイトプラットフォーム上にカスタマイズされたツールを作成できる api のコレクションです。 このページでは、作業の開始に役立つ概要を説明します。

## <a name="obtaining-the-sdk"></a>SDK の入手

次の手順にC++従って、BUILD Insights SDK を NuGet パッケージとしてダウンロードできます。

1. Visual Studio 2017 以降で、新しいC++プロジェクトを作成します。
1. **ソリューションエクスプローラー**ウィンドウで、プロジェクトを右クリックします。
1. コンテキストメニューの **[NuGet パッケージの管理]** を選択します。
1. 右上で、 **nuget.org**パッケージソースを選択します。
1. BuildInsights パッケージの最新バージョンを検索します。
1. **[インストール]** を選択します。
1. ライセンスに同意します。

SDK に関する一般的な概念については、「」を参照してください。 また、公式[ C++の Build Insights サンプル GitHub リポジトリ](https://github.com/microsoft/cpp-build-insights-samples)にアクセスして、SDK をC++使用する実際のアプリケーションの例を確認することもできます。

## <a name="collecting-a-trace"></a>トレースの収集

C++ BUILD Insights SDK を使用して MSVC ツールチェーンからのイベントを分析するには、最初にトレースを収集する必要があります。 SDK は、基になるトレーステクノロジとして Windows イベントトレーシング (ETW) を使用します。 トレースの収集は、次の2つの方法で行うことができます。

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>方法 1: Visual Studio 2019 以降で vcperf を使用する

1. VS 2019 の管理者特権の x64 Native Tools コマンドプロンプトを開きます。
1. 次のコマンドを実行します。 `vcperf /start MySessionName`
1. プロジェクトをビルドします。
1. 次のコマンドを実行します。 `vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > Vcperf でトレースを停止するときは、`/stopnoanalyze` コマンドを使用します。 C++ BUILD Insights SDK を使用して、通常の `/stop` コマンドによって停止されたトレースを分析することはできません。

### <a name="method-2-programmatically"></a>方法 2: プログラムによる

これらC++のいずれかの BUILD Insights SDK トレースコレクション関数を使用して、プログラムでトレースを開始および停止します。 **これらの関数呼び出しを実行するプログラムには、管理者特権が必要です。** 開始および停止トレース関数にのみ、管理者特権が必要です。 C++ビルドインサイト SDK 内の他のすべての関数は、使用せずに実行できます。

### <a name="sdk-functions-related-to-trace-collection"></a>トレースコレクションに関連する SDK 関数

| 機能 | C++ API | C API |
|--|--|--|
| トレースの開始 | [StartTracingSession](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| トレースの停止 | [StopTracingSession](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| トレースの停止と<br />結果をすぐに分析する | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| トレースの停止と<br />結果のログを直ちに再記録する | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

次のセクションでは、分析または再ログセッションを構成する方法について説明します。 これは、 [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md)などの機能の組み合わせに必要な機能です。

## <a name="consuming-a-trace"></a>トレースの使用

ETW トレースを取得したら、 C++ BUILD Insights SDK を使用してアンパックします。 SDK では、ツールをすばやく開発するための形式でイベントを提供します。 SDK を使用せずに生の ETW トレースを使用することはお勧めしません。 MSVC で使用されるイベント形式はドキュメント化されておらず、大規模なビルドに拡張できるように最適化されています。 また、ビルドC++インサイト SDK API は安定していますが、生の ETW トレース形式は予告なしに変更される可能性があります。

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>トレースの使用に関連する SDK の種類と関数

| 機能 | C++ API | C API | メモ |
|--|--|--|--|
| イベントコールバックの設定 | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | ビルドC++インサイト SDK は、コールバック関数を介してイベントを提供します。 でC++は、ianalyzer インターフェイスまたは irelogger インターフェイスを継承するアナライザーまたは relogger クラスを作成することによって、コールバック関数を実装します。 C では、コールバックをグローバル関数で実装し、ANALYSIS_CALLBACKS または RELOG_CALLBACKS 構造体にポインターを提供します。 |
| グループの作成 | [MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakeStaticReloggerGroup](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerGroup](functions/make-dynamic-relogger-group.md) |  | このC++ API には、複数のアナライザーと再ロガーオブジェクトをグループ化するためのヘルパー関数と型が用意されています。 グループは、複雑な分析をより簡単な手順に分割するための便利な方法です。 [vcperf](https://github.com/microsoft/vcperf)はこのように編成されています。 |
| 分析または再ログ | [分析](functions/analyze.md)<br />[Relog](functions/relog.md) | [Analyze Ea](functions/analyze-a.md)<br />[新規分析](functions/analyze-w.md)<br />[RelogA](functions/relog-a.md)<br />[RelogW](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>分析と再ログ

トレースは、分析セッションまたは再ログセッションのいずれかを使用して実行されます。

通常の分析を使用することは、ほとんどのシナリオに適しています。 この方法を使用すると、テキスト、xml、JSON、データベース、REST 呼び出しなどの `printf` の出力形式を柔軟に選択できます。

再ログは、ETW 出力ファイルを生成する必要がある特殊な目的の分析に使用されます。 再ログ記録を使用すると、 C++ Build Insights のイベントを独自の ETW イベント形式に変換できます。 再ログ記録を適切に使用するにはC++ 、既存の ETW ツールとインフラストラクチャにビルドインサイトデータをフックする必要があります。 たとえば、 [vcperf](https://github.com/microsoft/vcperf)は再ログインターフェイスを使用します。 これは、ETW ツールが理解できる Windows パフォーマンスアナライザーによってデータを生成する必要があるためです。 再ログインターフェイスの使用を計画している場合は、ETW のしくみに関する以前の知識が必要です。

### <a name="creating-analyzer-groups"></a>Analyzer グループの作成

グループの作成方法について理解しておくことが重要です。 *Hello, world!* を出力するアナライザーグループを作成する例を次に示します。 すべてのアクティビティ開始イベントが受信されます。

```cpp
using namespace Microsoft::Cpp::BuildInsights;

class Hello : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "Hello, " << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

class World : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "world!" << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

int main()
{
    Hello hello;
    World world;

    // Let's make Hello the first analyzer in the group
    // so that it receives events and prints "Hello, "
    // first.
    auto group = MakeStaticAnalyzerGroup(&hello, &world);

    unsigned numberOfAnalysisPasses = 1;

    // Calling this function initiates the analysis and
    // forwards all events from "inputTrace.etl" to my analyzer
    // group.
    Analyze("inputTrace.etl", numberOfAnalysisPasses, group);

    return 0;
}
```

## <a name="using-events"></a>イベントの使用

### <a name="sdk-types-and-functions-related-to-events"></a>イベントに関連する SDK の種類と関数

| 機能 | C++ API | C API | メモ |
|--|--|--|--|
| イベントの照合とフィルター処理 | [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack](functions/match-event-stack.md)<br />[MatchEventInMemberFunction](functions/match-event-in-member-function.md)<br />[MatchEvent](functions/match-event.md) |  | API C++には、トレースから、関心のあるイベントを簡単に抽出できるようにする関数が用意されています。 C API では、このフィルター処理を手動で行う必要があります。 |
| イベントデータ型 | [アクティビティ](cpp-event-data-types/activity.md)<br />[BackEndPass](cpp-event-data-types/back-end-pass.md)<br />[ボトムアップ](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[CodeGeneration](cpp-event-data-types/code-generation.md)<br />[Ds](cpp-event-data-types/command-line.md)<br />[コンパイラー](cpp-event-data-types/compiler.md)<br />[CompilerPass](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[イベント](cpp-event-data-types/event.md)<br />[EventGroup](cpp-event-data-types/event-group.md)<br />[EventStack](cpp-event-data-types/event-stack.md)<br />[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md)<br />[出力の出力](cpp-event-data-types/exp-output.md)<br />[FileInput](cpp-event-data-types/file-input.md)<br />[FileOutput](cpp-event-data-types/file-output.md)<br />[ForceInlinee](cpp-event-data-types/force-inlinee.md)<br />[FrontEndFile](cpp-event-data-types/front-end-file.md)<br />[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass](cpp-event-data-types/front-end-pass.md)<br />[Function](cpp-event-data-types/function.md)<br />[ImpLibOutput](cpp-event-data-types/imp-lib-output.md)<br />[[呼び出し]](cpp-event-data-types/invocation.md)<br />[InvocationGroup](cpp-event-data-types/invocation-group.md)<br />[LibOutput](cpp-event-data-types/lib-output.md)<br />[リンカー](cpp-event-data-types/linker.md)<br />[LinkerGroup](cpp-event-data-types/linker-group.md)<br />[LinkerPass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjOutput](cpp-event-data-types/obj-output.md)<br />[Opf](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[Pass1](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[SymbolName](cpp-event-data-types/symbol-name.md)<br />[TemplateInstantiation インスタンス化](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup](cpp-event-data-types/template-instantiation-group.md)<br />[スレッド](cpp-event-data-types/thread.md)<br />[TopDown](cpp-event-data-types/top-down.md)<br />[TraceInfo](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>アクティビティと単純なイベント

イベントには、*アクティビティ*と*単純なイベント*の2つのカテゴリがあります。 アクティビティは、開始と終了を含む継続的なプロセスです。 単純なイベントは punctual に発生し、期間はありません。 C++ BUILD Insights SDK を使用して MSVC トレースを分析する場合、アクティビティの開始時と停止時に個別のイベントを受け取ります。 単純なイベントが発生した場合は、イベントを1つだけ受け取ります。

### <a name="parent-child-relationships"></a>親子関係

アクティビティと単純なイベントは、親子関係を介して相互に関連付けられます。 アクティビティまたは単純なイベントの親は、そのアクティビティが発生する外側のアクティビティです。 たとえば、ソースファイルをコンパイルするときに、コンパイラはファイルを解析し、コードを生成する必要があります。 解析アクティビティとコード生成アクティビティは、どちらもコンパイラアクティビティの子です。

単純なイベントには期間がないため、その中に他のイベントが発生することはありません。 そのため、子は存在しません。

各アクティビティと単純なイベントの親子関係は、[イベントテーブル](event-table.md)に示されます。 C++ビルドインサイトイベントを使用する場合、これらの関係を把握することが重要です。 イベントの完全なコンテキストを理解するには、多くの場合、それらに依存する必要があります。

### <a name="properties"></a>Properties

すべてのイベントには、次のプロパティがあります。

| プロパティ | Description |
|--|--|
| 型識別子 | イベントの種類を一意に識別する番号。 |
| インスタンス識別子 | トレース内のイベントを一意に識別する番号。 トレースで同じ種類の2つのイベントが発生した場合は、どちらも一意のインスタンス識別子を取得します。 |
| 開始時刻 | アクティビティが開始された時刻、または単純なイベントが発生した時刻。 |
| プロセス識別子 | イベントが発生したプロセスを識別する番号。 |
| スレッド識別子 | イベントが発生したスレッドを識別する番号。 |
| プロセッサインデックス | イベントが生成された論理プロセッサを示す0から始まるインデックス。 |
| イベント名 | イベントの種類を説明する文字列。 |

単純なイベント以外のすべてのアクティビティには、次のプロパティもあります。

| プロパティ | Description |
|--|--|
| 停止時刻 | アクティビティが停止した時刻。 |
| 排他継続時間 | アクティビティに費やされた時間。子アクティビティに費やされた時間は含まれません。 |
| CPU 時間 | アクティビティにアタッチされているスレッド内のコードの実行に CPU が費やした時間。 アクティビティにアタッチされたスレッドがスリープ状態であった時間は含まれません。 |
| 排他 CPU 時間 | CPU 時間と同じですが、子アクティビティによって消費される CPU 時間は含まれません。 |
| ウォールクロックの時間責任 | 全体的なウォールクロック時間に対するアクティビティの影響。 ウォールクロックの責任には、アクティビティ間の並列処理が考慮されます。 たとえば、2つの関連のないアクティビティを並行して実行するとします。 どちらの期間も10秒で、開始時刻と終了時刻がまったく同じになります。 この場合、Build Insights は5秒間のウォールクロックの時間を割り当てます。 これに対して、これらのアクティビティが重複せずに1つずつ実行された場合は、どちらにも10秒のウォールクロック時間が割り当てられています。 |
| 排他的なウォール-クロック時間の責任 | ウォールクロックの時間責任と同じですが、子アクティビティのウォールクロックの時間責任は含まれません。 |

一部のイベントには、ここで説明した以外のプロパティがあります。 この場合、これらの追加のプロパティは[イベントテーブル](event-table.md)に一覧表示されます。

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>Build Insights SDK によっC++て提供されるイベントの使用

#### <a name="the-event-stack"></a>イベントスタック

ビルドインC++サイト SDK によってイベントが提供されるたびに、スタックの形式になります。 スタックの最後のエントリは、現在のイベントと、その親階層の前のエントリです。 たとえば、 [LTCG](event-table.md#ltcg) start イベントと stop イベントは、リンカーのパス1で発生します。 この場合、受信したスタックには \[[リンカー](event-table.md#linker)、 [PASS1](event-table.md#pass1)、LTCG\]が含まれます。 親階層は、ルートに対してイベントをトレースできるので便利です。 前述した LTCG アクティビティの速度が遅い場合は、どのリンカー呼び出しが関係していたかをすぐに知ることができます。

#### <a name="matching-events-and-event-stacks"></a>一致するイベントとイベントスタック

C++ BUILD Insights SDK では、トレース内のすべてのイベントが提供されますが、ほとんどの場合、それらのサブセットのみが考慮されます。 場合によっては、*イベントスタック*のサブセットのみが気になることがあります。 SDK には、必要なイベントやイベントスタックをすばやく抽出して、不要なイベントやイベントスタックを拒否する機能が用意されています。 これは、次の一致する関数によって行われます。

|  |  |
|--|--|
| [MatchEvent](functions/match-event.md) | 指定した型のいずれかと一致する場合は、イベントを保持します。 一致するイベントをラムダまたはその他の呼び出し可能な型に転送します。 イベントの親階層は、この関数では考慮されません。 |
| [MatchEventInMemberFunction](functions/match-event-in-member-function.md) | メンバー関数のパラメーターに指定されている型と一致する場合は、イベントを保持します。 一致したイベントをメンバー関数に転送します。 イベントの親階層は、この関数では考慮されません。 |
| [MatchEventStack](functions/match-event-stack.md) | イベントとその親階層の両方が指定された型と一致する場合は、イベントを保持します。 イベントと、一致した親階層イベントを、ラムダまたはその他の呼び出し可能な型に転送します。 |
| [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md) | イベントとその親階層の両方が、メンバー関数のパラメーターリストで指定されている型と一致する場合は、イベントを保持します。 イベントと、一致した親階層イベントをメンバー関数に転送します。 |

`MatchEventStack` のようなイベントスタック一致関数は、一致させる親階層を記述するときにギャップを許可します。 たとえば、\[[リンカー](event-table.md#linker)、 [LTCG](event-table.md#ltcg)\] stack に関心があるとします。 また、\[リンカー、 [PASS1](event-table.md#pass1)、LTCG\] stack とも一致します。 指定する最後の型は、一致させるイベントの種類である必要があり、親階層の一部ではありません。

#### <a name="capture-classes"></a>キャプチャクラス

`Match*` 関数を使用するには、一致させる型を指定する必要があります。 これらの型は、*キャプチャクラス*の一覧から選択されます。 キャプチャクラスには、次に示すいくつかのカテゴリがあります。

| カテゴリ | Description |
|--|--|
| [Exact] | これらのキャプチャクラスは、特定のイベントの種類を照合するために使用され、その他は使用されません。 例と[して、コンパイライベントに](event-table.md#compiler)一致する[コンパイラ](cpp-event-data-types/compiler.md)クラスがあります。 |
| ワイルドカード | これらのキャプチャクラスを使用して、サポートするイベントの一覧から任意のイベントを照合できます。 たとえば、[アクティビティ](cpp-event-data-types/activity.md)のワイルドカードは、任意のアクティビティイベントと一致します。 もう1つの例として、 [CompilerPass](cpp-event-data-types/compiler-pass.md)ワイルドカードがあります。これは、 [FRONT_END_PASS](event-table.md#front-end-pass)または[BACK_END_PASS](event-table.md#back-end-pass)イベントに一致できます。 |
| Group | グループキャプチャクラスの名前は*グループ*で終了します。 これらは、行で同じ種類の複数のイベントを照合するために使用されます。ギャップは無視されます。 イベントスタックに存在する数がわからないため、再帰的なイベントと一致する場合にのみ意味があります。 たとえば、 [FRONT_END_FILE](event-table.md#front-end-file)アクティビティは、コンパイラがファイルを解析するたびに発生します。 このアクティビティは再帰的です。これは、コンパイラがファイルの解析中に include ディレクティブを見つけられる可能性があるためです。 [Frontendfile](cpp-event-data-types/front-end-file.md)クラスは、スタック内の1つの FRONT_END_FILE イベントにのみ一致します。 インクルード階層全体に一致させるには、 [Frontendfilegroup](cpp-event-data-types/front-end-file-group.md)クラスを使用します。 |
| ワイルドカードグループ | ワイルドカードグループは、ワイルドカードとグループのプロパティを組み合わせたものです。 このカテゴリの唯一のクラスは[InvocationGroup](cpp-event-data-types/invocation-group.md)であり、すべての[リンカー](event-table.md#linker)および[コンパイラ](event-table.md#compiler)イベントを1つのイベントスタックに一致させてキャプチャします。 |

各イベントの照合に使用できるキャプチャクラスについては、[イベントテーブル](event-table.md)を参照してください。

#### <a name="after-matching-using-captured-events"></a>照合後: キャプチャしたイベントの使用

一致が正常に完了すると、`Match*` 関数は、キャプチャクラスのオブジェクトを構築し、指定された関数に転送します。 これらのキャプチャクラスオブジェクトを使用して、イベントのプロパティにアクセスします。

#### <a name="example"></a>例

```cpp
AnalysisControl MyAnalyzer::OnStartActivity(const EventStack& eventStack)
{
    // The event types to match are specified in the PrintIncludes function
    // signature.  
    MatchEventStackInMemberFunction(eventStack, this, &MyAnalyzer::PrintIncludes);
}

// We want to capture event stacks where:
// 1. The current event is a FrontEndFile activity.
// 2. The current FrontEndFile activity has at least one parent FrontEndFile activity
//    and possibly many.
void PrintIncludes(FrontEndFileGroup parentIncludes, FrontEndFile currentFile)
{
    // Once we reach this point, the event stack we are interested in has been matched.
    // The current FrontEndFile activity has been captured into 'currentFile', and
    // its entire inclusion hierarchy has been captured in 'parentIncludes'.

    cout << "The current file being parsed is: " << currentFile.Path() << endl;
    cout << "This file was reached through the following inclusions:" << endl;

    for (auto& f : parentIncludes)
    {
        cout << f.Path() << endl;
    }
}
```

::: moniker-end
