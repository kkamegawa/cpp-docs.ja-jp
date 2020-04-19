---
title: allocator
ms.date: 03/21/2019
f1_keywords:
- allocator_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocator
- allocator __declspec keyword
ms.openlocfilehash: 2e2615829f6491bf660859fbc86ebcd07a56c5fe
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857685"
---
# <a name="allocator"></a>allocator

**Microsoft 固有の仕様**

**allocator**宣言指定子は、割り当てを使用して Event Tracing for Windows (ETW) 表示するカスタムのメモリ割り当て関数に適用できます。

## <a name="syntax"></a>構文

```
   __declspec(allocator) 
```

## <a name="remarks"></a>Remarks

Visual Studio のネイティブメモリプロファイラーは、実行時にによって出力された割り当て ETW イベントデータを収集することによって機能します。 CRT および Windows SDK のアロケーターには、割り当てデータをキャプチャできるように、ソース レベルで注釈が付けられています。 独自のアロケーターを作成する場合、新しく割り当てられたヒープメモリへのポインターを返す関数は、次の myMalloc の例に示すように、`__declspec(allocator)`で修飾できます。

```cpp
__declspec(allocator) void* myMalloc(size_t size)
```

詳細については、「 [Visual Studio でのメモリ使用量の測定](/visualstudio/profiling/memory-usage)」と「[カスタムネイティブ ETW ヒープイベント](/visualstudio/profiling/custom-native-etw-heap-events)」を参照してください。

**Microsoft 固有の仕様はここまで**
