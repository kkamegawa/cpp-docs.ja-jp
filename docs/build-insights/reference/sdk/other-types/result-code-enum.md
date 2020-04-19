---
title: RESULT_CODE 列挙型
description: C++ビルドインサイト SDK RESULT_CODE 列挙型参照です。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RESULT_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ee563d148b3456b288bc418255ec46f8cbade7ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333948"
---
# <a name="result_code-enum"></a>RESULT_CODE 列挙型

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`RESULT_CODE` 列挙型は、成功と失敗の条件を記述します。

## <a name="members"></a>メンバー

| Name | 値 | Description |
|--|--|--|
| `RESULT_CODE_SUCCESS` | 0 (0x00000000) | 操作は成功しました。 |
| `RESULT_CODE_FAILURE_ANALYSIS_ERROR` | 1 (0x00000001) | [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)または[RELOG_DESCRIPTOR](relog-descriptor-struct.md)のいずれかのコールバック関数が `CALLBACK_CODE_ANALYSIS_FAILURE` 値を返しました。 この値は[CALLBACK_CODE](callback-code-enum.md)列挙型のメンバーです。 |
| `RESULT_CODE_FAILURE_CANCELLED` | 2 (0x00000002) | [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)または[RELOG_DESCRIPTOR](relog-descriptor-struct.md)のいずれかのコールバック関数が `CALLBACK_CODE_ANALYSIS_CANCEL` 値を返しました。 この値は[CALLBACK_CODE](callback-code-enum.md)列挙型のメンバーです。 |
| `RESULT_CODE_FAILURE_INVALID_INPUT_LOG_FILE` | 3 (0x00000003) | 指定された入力 Windows イベントトレーシング (ETW) トレースが無効です。 |
| `RESULT_CODE_FAILURE_INVALID_OUTPUT_LOG_FILE` | 4 (0x00000004) | 指定された出力 ETW トレースは無効です。 |
| `RESULT_CODE_FAILURE_MISSING_ANALYSIS_CALLBACK` | 5 (0x00000005) | [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)構造が正しく初期化されませんでした。 |
| `RESULT_CODE_FAILURE_MISSING_RELOG_CALLBACK` | 6 (0x00000006) | [RELOG_CALLBACKS](relog-callbacks-struct.md)構造が正しく初期化されませんでした。 |
| `RESULT_CODE_FAILURE_OPEN_INPUT_TRACE` | 7 (0x00000007) | 入力 ETW トレースを開くことができませんでした。 |
| `RESULT_CODE_FAILURE_PROCESS_TRACE` | 8 (0x00000008) | 入力 ETW トレースの処理中にエラーが発生しました。 |
| `RESULT_CODE_FAILURE_START_RELOGGER` | 9 (0x00000009) | 再ログセッションを開始しようとしたときにエラーが発生しました。 |
| `RESULT_CODE_FAILURE_DROPPED_EVENTS` | 10 (0x0000000A) | 入力 ETW トレースに重要なイベントがありません。 |
| `RESULT_CODE_FAILURE_UNSUPPORTED_OS` | 11 (0x0000000B) | サポートされC++ていないバージョンの Windows でビルドインサイトを使用しています。 |
| `RESULT_CODE_FAILURE_INVALID_TRACING_SESSION_NAME` | 12 (0x0000000C) | 指定されたセッション名は無効です。 |
| `RESULT_CODE_FAILURE_INSUFFICIENT_PRIVILEGES` | 13 (0x0000000D) | この操作には管理者特権が必要です。 |
| `RESULT_CODE_FAILURE_GENERATE_GUID` | 14 (0x0000000E) | GUID の生成中にエラーが発生しました。 |
| `RESULT_CODE_FAILURE_OBTAINING_TEMP_DIRECTORY` | 15 (0x0000000F) | 一時ディレクトリのパスを確認中にエラーが発生しました。 |
| `RESULT_CODE_FAILURE_CREATE_TEMPORARY_DIRECTORY` | 16 (0x00000010) | 開始中のトレースセッションの一時ディレクトリを作成しようとして、エラーが発生しました。 |
| `RESULT_CODE_FAILURE_START_SYSTEM_TRACE` | 17 (0x00000011) | システムトレースを開始しようとしたときにエラーが発生しました。 |
| `RESULT_CODE_FAILURE_START_MSVC_TRACE` | 18 (0x00000012) | MSVC トレースを開始しようとしたときにエラーが発生しました。 |
| `RESULT_CODE_FAILURE_STOP_MSVC_TRACE` | 19 (0x00000013) | MSVC トレースを停止しようとしたときにエラーが発生しました。 |
| `RESULT_CODE_FAILURE_STOP_SYSTEM_TRACE` | 20 (0x00000014) | システムトレースを開始しようとしたときにエラーが発生しました。 |
| `RESULT_CODE_FAILURE_SESSION_DIRECTORY_RESOLUTION` | 21 (0x00000015) | トレースが停止されましたが、トレースセッションの一時ディレクトリが見つかりません。 |
| `RESULT_CODE_FAILURE_MSVC_TRACE_FILE_NOT_FOUND` | 22 (0x00000016) | 停止しようとしている MSVC トレースのトレースファイルが見つかりません。 |
| `RESULT_CODE_FAILURE_MERGE_TRACES` | 23 (0x00000017) | カーネルトレースコントロールを使用してトレースをマージするときにエラーが発生しました。 |
| `RESULT_CODE_FAILURE_UNKNOWN_ERROR` | 24 (0x00000018) | 不明なエラーが発生しました。 |

::: moniker-end
