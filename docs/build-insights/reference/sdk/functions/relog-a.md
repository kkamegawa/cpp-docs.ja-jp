---
title: RelogA
description: ビルドC++インサイト SDK は関数参照を再作成します。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RelogA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c4427aa0ac85e34bfb9d569913a8ccf6ab264f52
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334320"
---
# <a name="reloga"></a>RelogA

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`RelogA` 関数は、Windows イベントトレーシング (ETW) トレースから MSVC イベントを読み取り、それを新しい変更された ETW トレースに書き込むために使用されます。

## <a name="syntax"></a>構文

```cpp
enum RESULT_CODE RelogA(
    const char*             inputLogFile,
    const char*             outputLogFile,
    const RELOG_DESCRIPTOR* relogDescriptor);
```

### <a name="parameters"></a>パラメーター

*Inputlogfile*\
イベントの読み取り元の入力 ETW トレース。

*Outputlogfile*\
新しいイベントを書き込むファイル。

*Relogdescriptor*\
[RELOG_DESCRIPTOR](../other-types/relog-descriptor-struct.md)オブジェクトへのポインター。 このオブジェクトを使用して、再ログセッションを構成します。

### <a name="return-value"></a>戻り値

[RESULT_CODE](../other-types/result-code-enum.md)列挙型の結果コード。

::: moniker-end
