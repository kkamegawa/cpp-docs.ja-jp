---
title: リンカー ツールの警告 LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 3d89b27c32b33b917abb7fc140eebf5924142423
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298543"
---
# <a name="linker-tools-warning-lnk4104"></a>リンカー ツールの警告 LNK4104

シンボル 'symbol' のエクスポートがプライベートにする必要があります。

`symbol`次のいずれかを指定できます。

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllGetDocumentation`

- `DllInitialize`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllRegisterServerExW`

- `DllUnload`

- `DllUnregisterServer`

- `RasCustomDeleteEntryNotify`

- `RasCustomDial`

- `RasCustomDialDlg`

- `RasCustomEntryDlg`

この警告は、dll インポート ライブラリを構築するときに生成され、モジュール定義ファイル内のプライベートとして指定せずに、上記の関数のいずれかをエクスポートします。 一般に、これらの関数は、OLE でのみ使用するためエクスポートされます。 リンクされているライブラリを正しくプログラムがそれらへの呼び出しを行うと、インポート ライブラリに配置するは異常な動作につながります。 PRIVATE キーワードの詳細については、次を参照してください。[エクスポート](../../build/reference/exports.md)します。