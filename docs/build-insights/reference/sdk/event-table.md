---
title: 'C++Build Insights SDK: イベントテーブル'
description: Visual Studio C++ BUILD Insights SDK のイベントリファレンス
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2ccc8a4ef707942963b85edc6db9e21e05610b54
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857012"
---
# <a name="c-build-insights-sdk-event-table"></a>C++Build Insights SDK: イベントテーブル

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>コンパイライベント

[コンパイラ](#compiler)の\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[OBJ_OUTPUT](#obj-output)\
[FRONT_END_PASS](#front-end-pass)\
[BACK_END_PASS](#back-end-pass)

## <a name="compiler-front-end-events"></a>コンパイラのフロントエンドイベント

[C1_DLL](#c1-dll)\
[FRONT_END_FILE](#front-end-file)\
[TEMPLATE_INSTANTIATION](#template-instantiation)\
[SYMBOL_NAME](#symbol-name)

## <a name="compiler-back-end-events"></a>コンパイラのバックエンドイベント

[C2_DLL](#c2-dll)\
[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis)\
[TOP_DOWN](#top-down)\
[BOTTOM_UP](#bottom-up)\
[CODE_GENERATION](#code-generation)\
[スレッド](#thread)\
[関数](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>リンカーイベント

[リンカー](#linker)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[PASS1](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PASS2](#pass2)

## <a name="event-table"></a>イベントテーブル

| Event | プロパティ | Description |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | 種類 | アクティビティ |
|  | Parents | [コンパイラー](#compiler) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Properties | -入力ソースファイルへの絶対パス<br/>-出力オブジェクトファイルへの絶対パス |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[BackEndPass](cpp-event-data-types/back-end-pass.md) |
|  | Description | コンパイラのバックエンドパスの開始時と終了時に発生します。 このパスは、解析された CC++ /ソースコードを最適化し、マシンコードに変換する役割を担います。 |
| <a name="bottom-up"></a>BOTTOM_UP | 種類 | アクティビティ |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | なし |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[ボトムアップ](cpp-event-data-types/bottom-up.md) |
|  | Description | プログラム全体の分析の "最上位パス" の開始時と終了時に発生します。 |
| <a name="c1-dll"></a>C1_DLL | 種類 | アクティビティ |
|  | Parents | [FRONT_END_PASS](#front-end-pass) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | Description | は、 *c1 .dll*または*c1xx*の呼び出しの開始時と停止時に発生します。 これらの Dll は、コンパイラC++の C およびフロントエンドです。 これらのファイルは、コンパイラドライバー (*cl.exe*) によってのみ呼び出されます。 |
| <a name="c2-dll"></a>C2_DLL | 種類 | アクティビティ |
|  | Parents | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | Children | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | Description | は、 *c2 .dll*呼び出しの開始時と終了時に発生します。 この DLL は、コンパイラのバックエンドです。 コンパイラドライバー (*cl.exe*) によって呼び出されます。 また、リンク時のコード生成が使用されるときに、リンカー (*setup.exe*) によっても呼び出されます。 |
| <a name="code-generation"></a>CODE_GENERATION | 種類 | アクティビティ |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [FUNCTION](#function)<br/>[レッド](#thread) |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[CodeGeneration](cpp-event-data-types/code-generation.md) |
|  | Description | バックエンドのコード生成フェーズの開始時と終了時に発生します。 |
| <a name="command-line"></a>COMMAND_LINE | 種類 | 簡易イベント |
|  | Parents | [コンパイラー](#compiler)<br/>[リンカ](#linker) |
|  | Children | なし |
|  | Properties | - *Cl.exe*または*setup.exe*を起動するために使用されたコマンドライン |
|  | キャプチャクラス | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Ds](cpp-event-data-types/command-line.md) |
|  | Description | コンパイラとリンカーがコマンドラインの評価を完了したときに発生します。 評価されたコマンドラインには、すべての*cl.exe*と、応答ファイルを介して渡された*リンク .exe*パラメーターが含まれています。 また *、cl.exe のパラメーターと、* cl、\_cl\_、リンク、\_リンク\_などの環境変数を介して渡される*setup.exe*のパラメーターも含まれます。 |
| <a name="compiler"></a>コンパイラー | 種類 | アクティビティ |
|  | Parents | なし |
|  | Children | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | Properties | -コンパイラのバージョン<br/>-作業ディレクトリ<br/>-呼び出された*cl.exe*の絶対パス |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[[呼び出し]](cpp-event-data-types/invocation.md)<br/>[コンパイラー](cpp-event-data-types/compiler.md) |
|  | Description | *Cl.exe*呼び出しの開始時と終了時に発生します。 |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | 種類 | 簡易イベント |
|  | Parents | [コンパイラー](#compiler)<br/>[リンカ](#linker) |
|  | Children | なし |
|  | Properties | -環境変数の名前<br/>-環境変数の値。 |
|  | キャプチャクラス | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | Description | *Cl.exe*または*client.exe*が呼び出されたときに、すべての既存の環境変数に対して1回発生します。 |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | 種類 | 簡易イベント |
|  | Parents | [リンカ](#linker) |
|  | Children | なし |
|  | Properties | -DLL または実行可能な出力ファイルへの絶対パス。 |
|  | キャプチャクラス | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | Description | リンカー入力の1つが DLL または実行可能イメージファイルの場合に発生します。 |
| <a name="exp-output"></a>EXP_OUTPUT | 種類 | 簡易イベント |
|  | Parents | [リンカ](#linker) |
|  | Children | なし |
|  | Properties | - *.Exp*出力ファイルへの絶対パス。 |
|  | キャプチャクラス | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[出力の出力](cpp-event-data-types/exp-output.md) |
|  | Description | リンカー出力の1つが *.exp*ファイルの場合に発生します。 |
| <a name="file-input"></a>FILE_INPUT | 種類 | 簡易イベント |
|  | Parents | [コンパイラー](#compiler)<br/>[リンカ](#linker) |
|  | Children | なし |
|  | Properties | -入力ファイルへの絶対パス<br/>-入力ファイルの種類 |
|  | キャプチャクラス | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileInput](cpp-event-data-types/file-input.md) |
|  | Description | *Cl.exe*または*cmd.exe*の入力をアナウンスするために発生します。 |
| <a name="force-inlinee"></a>FORCE_INLINEE | 種類 | 簡易イベント |
|  | Parents | [FUNCTION](#function) |
|  | Children | なし |
|  | Properties | -強制インライン関数の名前。<br/>-中間命令数として表される強制インライン関数のサイズ。 |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[ForceInlinee](cpp-event-data-types/force-inlinee.md) |
|  | Description | `__forceinline` キーワードを使用して、関数が別の関数に強制的にインライン展開されるときに発生します。 |
| <a name="front-end-file"></a>FRONT_END_FILE | 種類 | アクティビティ |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Properties | -ファイルの絶対パス。 |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[FrontEndFile](cpp-event-data-types/front-end-file.md) |
|  | Description | コンパイラのフロントエンドが開始し、ファイルの処理を停止したときに発生します。 このイベントは再帰的です。 再帰は、フロントエンドがインクルードファイルを解析しているときに発生します。 |
| <a name="front-end-pass"></a>FRONT_END_PASS | 種類 | アクティビティ |
|  | Parents | [コンパイラー](#compiler) |
|  | Children | [C1_DLL](#c1-dll) |
|  | Properties | -入力ソースファイルへの絶対パス<br/>-出力オブジェクトファイルへの絶対パス |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[FrontEndPass](cpp-event-data-types/front-end-pass.md) |
|  | Description | コンパイラのフロントエンドパスの開始時と停止時に発生します。 このパスは、C/C++ソースコードを解析し、それを中間言語に変換する役割を担います。 |
| <a name="function"></a>プロシージャ | 種類 | アクティビティ |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[レッド](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FORCE_INLINEE](#force-inlinee) |
|  | Properties | -関数の名前 |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[Function](cpp-event-data-types/function.md) |
|  | Description | 関数のコードの生成を開始および終了したときに発生します。 |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | 種類 | 簡易イベント |
|  | Parents | [リンカ](#linker) |
|  | Children | なし |
|  | Properties | -インポートライブラリの出力ファイルへの絶対パス。 |
|  | キャプチャクラス | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput](cpp-event-data-types/imp-lib-output.md) |
|  | Description | リンカーの出力の1つがインポートライブラリの場合に発生します。 |
| <a name="lib-output"></a>LIB_OUTPUT | 種類 | 簡易イベント |
|  | Parents | [リンカ](#linker) |
|  | Children | なし |
|  | Properties | -スタティックライブラリ出力ファイルへの絶対パス。 |
|  | キャプチャクラス | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[LibOutput](cpp-event-data-types/lib-output.md) |
|  | Description | リンカーの出力の1つがスタティックライブラリの場合に発生します。 |
| <a name="linker"></a>リンカ | 種類 | アクティビティ |
|  | Parents | なし |
|  | Children | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PASS1](#pass1)<br/>[PASS2](#pass2) |
|  | Properties | -リンカーのバージョン<br/>-作業ディレクトリ<br/>-呼び出された*リンク*の絶対パス |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[[呼び出し]](cpp-event-data-types/invocation.md)<br/>[リンカー](cpp-event-data-types/linker.md) |
|  | Description | *リンクの .exe*呼び出しの開始時と終了時に発生します。 |
| <a name="ltcg"></a>LTCG | 種類 | アクティビティ |
|  | Parents | [PASS1](#pass1) |
|  | Children | [C2_DLL](#c2-dll) |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | Description | リンク時のコード生成の開始時と終了時に発生します。 |
| <a name="obj-output"></a>OBJ_OUTPUT | 種類 | 簡易イベント |
|  | Parents | [コンパイラー](#compiler) |
|  | Children | なし |
|  | Properties | - *.Obj*出力ファイルへの絶対パス |
|  | キャプチャクラス | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ObjOutput](cpp-event-data-types/obj-output.md) |
|  | Description | *Cl.exe*によって生成されるすべての *.obj*出力に対して1回発生します。 |
| <a name="opt-icf"></a>OPT_ICF | 種類 | アクティビティ |
|  | Parents | [PASS1](#pass1) |
|  | Children | なし |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[Opf](cpp-event-data-types/opt-icf.md) |
|  | Description | 同じ COMDAT フォールド (/OPT: ICF) リンカーの最適化の開始時と終了時に発生します。 |
| <a name="opt-lbr"></a>OPT_LBR | 種類 | アクティビティ |
|  | Parents | [PASS1](#pass1) |
|  | Children | なし |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | Description | Long branch (/OPT: LBR) リンカーの最適化の開始時と停止時に発生します。 |
| <a name="opt-ref"></a>OPT_REF | 種類 | アクティビティ |
|  | Parents | [PASS1](#pass1) |
|  | Children | なし |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | Description | 参照されていない関数とデータ削除 (/OPT: REF) リンカーの最適化の開始時および停止時に発生します。 |
| <a name="pass1"></a>PASS1 | 種類 | アクティビティ |
|  | Parents | [リンカ](#linker) |
|  | Children | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[Pass1](cpp-event-data-types/pass1.md) |
|  | Description | リンカーのパス1の開始時と停止時に発生します。 |
| <a name="pass2"></a>PASS2 | 種類 | アクティビティ |
|  | Parents | [リンカ](#linker) |
|  | Children | なし |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[Pass2](cpp-event-data-types/pass2.md) |
|  | Description | リンカーのパス2の開始時と終了時に発生します。 |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | 種類 | アクティビティ |
|  | Parents | [PASS1](#pass1) |
|  | Children | なし |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | Description | 参照されていない関数とデータ (/OPT: REF) を排除する、リンカー最適化パスの開始時および停止時に発生します。 これは、リンク時のコード生成の前に行われます。 |
| <a name="symbol-name"></a>SYMBOL_NAME | 種類 | 簡易イベント |
|  | Parents | [C1_DLL](#c1-dll) |
|  | Children | なし |
|  | Properties | -型キー<br/> -型の名前 |
|  | キャプチャクラス | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[SymbolName](cpp-event-data-types/symbol-name.md) |
|  | Description | フロントエンドパスの最後で、テンプレートのインスタンス化に関係するすべての型につき1回発生します。 キーは型の数値識別子であり、名前はテキスト表現です。 型キーは、分析されるトレース内で一意です。 ただし、コンパイラのフロントエンドパスが異なると、異なるキーが同じ型を指している場合があります。 異なるコンパイラフロントエンドパス間で型を比較するには、その名前を使用する必要があります。 SYMBOL_NAME イベントは、すべてのテンプレートのインスタンス化が行われた後に、コンパイラのフロントエンドパスの最後に生成されます。 |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | 種類 | アクティビティ |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Children | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Properties | -特殊な型のキー<br/>-プライマリテンプレートの型のキー<br/>-インスタンス化されたテンプレートの種類 |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[TemplateInstantiation インスタンス化](cpp-event-data-types/template-instantiation.md) |
|  | Description | テンプレートのインスタンス化の開始時と終了時に発生します。 プライマリテンプレートの型 (`vector`など) はインスタンス化され、その結果、特殊な型 (`std::vector<int>`など) になります。 キーは両方の型に与えられます。 [SYMBOL_NAME](#symbol-name)イベントを使用して、キーを型の名前に変換します。 型キーは、分析されるトレース内で一意です。 ただし、コンパイラのフロントエンドパスが異なると、異なるキーが同じ型を指している場合があります。 異なるコンパイラフロントエンドパス間で型を比較するには、シンボル名を使用する必要があります。 このイベントは再帰的です。 再帰は、フロントエンドが入れ子になったテンプレートをインスタンス化している場合に発生します。 |
| <a name="thread"></a>レッド | 種類 | アクティビティ |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FUNCTION](#function) |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[スレッド](cpp-event-data-types/thread.md) |
|  | Description | コンパイラのバックエンドスレッドの実行の開始時と終了時に発生します。 中断されているスレッドは終了したと見なされます。 ウェイクアップされるスレッドは、開始済みと見なされます。 |
| <a name="top-down"></a>TOP_DOWN | 種類 | アクティビティ |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | [FUNCTION](#function)<br/>[レッド](#thread) |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[TopDown](cpp-event-data-types/top-down.md) |
|  | Description | プログラム全体の分析のトップダウンパスの開始時と終了時に発生します。 |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | 種類 | アクティビティ |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | Properties | なし |
|  | キャプチャクラス | [アクティビティ](cpp-event-data-types/activity.md)<br/>[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) |
|  | Description | リンク時のコード生成のプログラム全体の分析フェーズの開始時および停止時に発生します。 |

::: moniker-end
