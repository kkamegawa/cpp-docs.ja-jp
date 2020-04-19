---
title: コンパイラの警告 C4335
ms.date: 11/04/2016
f1_keywords:
- C4335
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
ms.openlocfilehash: ccb00118d0c6895eee84976bb01472ea2f98353d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627119"
---
# <a name="compiler-warning-c4335"></a>コンパイラの警告 C4335

Mac ファイル形式が検出されました: ソースファイルを DOS または UNIX 形式に変換してください

ソースファイルの最初の行の行終了文字は、UNIX (' \n ') または DOS ("\r\n") ではなく、Macintosh スタイル ("\r") です。

この警告は、常にエラーとして表示されます。  この警告を無効にする方法については、「 [warning](../../preprocessor/warning.md)プラグマ」を参照してください。  また、この警告は、コンパイル単位ごとに1回のみ発行されます。 したがって、Macintosh 形式でファイルを指定する複数の `#include` ディレクティブがある場合、C4335 は1回のみ発行されます。

Macintosh 形式でファイルを生成する方法の1つとして、Visual Studio の **[ファイル]** メニューの **[保存オプションの詳細設定]** を使用する方法があります。

## <a name="example"></a>例

次の例では、C4335 が生成されます。

```cpp
// C4335 expected
#include "c4335.h"   // assume both include files are in Macintosh format
#include "c4335_2.h"
```
