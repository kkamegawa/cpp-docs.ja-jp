---
title: リンカー ツールの警告 LNK4105
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 880c8519a530f492d0c322575a1386af8a7d0187
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310930"
---
# <a name="linker-tools-warning-lnk4105"></a>リンカー ツールの警告 LNK4105

オプション 'option'; で指定された引数がいません。オプションを無視します

のみでこの警告が発生したときに、 [/LIBPATH](../../build/reference/libpath-additional-libpath.md)オプションが設定されています。 このオプションでディレクトリが指定されていない、リンカーは、オプションを無視し、この警告メッセージが生成されます。

既存の環境のライブラリの設定をオーバーライドする必要がない場合は、リンカーのコマンドラインから/LIBPATH オプションを削除します。 ライブラリの別の検索パスを使用する場合は、/LIBPATH オプションに続く代替パスを指定します。

## <a name="example"></a>例

```
link /libpath:c:\filepath\lib bar.obj
```

必要なライブラリを検索するリンカーに指示が`c:\filepath\lib`の既定の場所で検索する前にします。