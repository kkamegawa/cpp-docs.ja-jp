---
title: FILE_TYPE_CODE 列挙型
description: C++ビルドインサイト SDK FILE_TYPE_CODE 列挙型参照です。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e64f9315c62ce40c436032d6c96fdfa725847a7f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335166"
---
# <a name="file_type_code-enum"></a>FILE_TYPE_CODE 列挙型

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`FILE_TYPE_CODE` 列挙型は、ファイルの種類を記述します。

## <a name="members"></a>メンバー

| Name | 値 | Description |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 (0x00000000) | この列挙に含まれていないファイルの種類。 |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | オブジェクト (\*.obj) ファイル。 |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 (0x00000002) | 実行可能ファイル (\*.exe) または DLL (\*.dll) ファイル。 |
| `FILE_TYPE_CODE_LIB` | 3 (0x00000003) | スタティックライブラリ (* .lib) ファイル。 |
| `FILE_TYPE_CODE_IMP_LIB` | 4 (0x00000004) | インポートライブラリ (* .lib) |
| `FILE_TYPE_CODE_EXP` | 5 (0x00000005) | エクスポート (* .exp) ファイル。 |

## <a name="remarks"></a>解説

::: moniker-end
