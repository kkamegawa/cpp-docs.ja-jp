---
title: ファイル属性定数
ms.date: 11/04/2016
f1_keywords:
- A_HIDDEN
- _A_NORMAL
- _A_SUBDIR
- _A_RDONLY
- A_NORMAL
- A_SUBDIR
- _A_SYSTEM
- c.constants.file
- _A_HIDDEN
- A_RDONLY
- _A_ARCH
- A_ARCH
helpviewer_keywords:
- constants [C++], file attributes
- file attribute constants [C++]
- _A_SYSTEM constant
- files [C++], file attribute constants
- _A_SUBDIR constant
- _A_ARCH constant
- _A_NORMAL constant
- _A_HIDDEN constant
- _A_RDONLY constant
ms.assetid: 8dc8ccb9-99f5-446b-876c-7ebecc2f764f
ms.openlocfilehash: 271459c33cdcc1110222871bdca06d3f04edb497
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750885"
---
# <a name="file-attribute-constants"></a>ファイル属性定数

## <a name="syntax"></a>構文

```
#include <io.h>
```

## <a name="remarks"></a>解説

これらの定数は、関数によって指定されたファイルまたはディレクトリの現在の属性を指定します。

属性は、次のマニフェスト定数によって表されます。

|定数|説明|
|-|-|
|`_A_ARCH`| アーカイブ。 BACKUP コマンドによってファイルが変更またはクリアされるたびに設定されます。 値: 0x20|
|`_A_HIDDEN`| 隠しファイル。 /AH オプションを使用しない限り、通常 DIR コマンドで見ることはできません。 この属性を持つファイルのほかに通常のファイルに関する情報を返します。 値: 0x02|
|`_A_NORMAL`| 標準。 制限なしにファイルの読み取りや書き込みができます。 値: 0x00|
|`_A_RDONLY`| 読み取り専用。 書き込み用にファイルを開くことや、同じ名前を持つファイルを作成することはできません。 値: 0x01|
|`_A_SUBDIR`| サブディレクトリ。 値: 0x10|
|`_A_SYSTEM`| システム ファイル。 /AS オプションを使用しない限り、通常 DIR コマンドで見ることはできません。 値: 0x04|

OR 演算子 (&#124;) を使用して、複数の定数を組み合わせることができます。

## <a name="see-also"></a>関連項目

[ファイル名検索関数](../c-runtime-library/filename-search-functions.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
