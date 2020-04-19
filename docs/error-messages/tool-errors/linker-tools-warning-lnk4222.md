---
title: リンカー ツールの警告 LNK4222
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: 52a4fee532eb9997dcf013f95246b27fdffc4c20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160407"
---
# <a name="linker-tools-warning-lnk4222"></a>リンカー ツールの警告 LNK4222

エクスポートされたシンボル 'symbol' に序数を割り当てないでください。

次の記号は、序数でエクスポートする必要がありません。

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

これらの関数は常に名前であるを使用して`GetProcAddress`します。 リンカーはこれについて警告エクスポートの種類と拡大画像が生じる可能性があるためです。 これは、序数でのエクスポートの範囲が比較的少ないエクスポートを含む大規模な場合に発生する可能性があります。 例えば以下のようにします。

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

100 のうち 98 にエクスポート アドレス テーブル (2 ~ 99) は単なる空白スロットを必要となります。 一方

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

2 つのスロットを必要となります。 (にもエクスポートできることに注意してください、 [/export](../../build/reference/export-exports-a-function.md)リンカー オプション)。