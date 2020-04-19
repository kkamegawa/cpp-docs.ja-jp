---
title: リンカー ツールの警告 LNK4098
description: 互換性のないライブラリがリンカーツールの警告 LNK4098 を生成する方法と、/NODEFAULTLIB を使用してそれを修正する方法について説明します。
ms.date: 12/02/2019
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 9d0c7da0614651a98d5ed4f3bd3676c7d837ce67
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "74682944"
---
# <a name="linker-tools-warning-lnk4098"></a>リンカー ツールの警告 LNK4098

> defaultlib '*library*' は他のライブラリの使用と競合しています。/NODEFAULTLIB:*library*の使用

互換性のないライブラリとリンクしようとしています。

> [!NOTE]
> ランタイムライブラリには、さまざまな型が混在しないようにするためのディレクティブが含まれるようになりました。 この警告は、同じプログラムで別の型を使用しようとした場合や、ランタイムライブラリのデバッグバージョンと非デバッグバージョンを使用しようとした場合に表示されます。 たとえば、ある種類のランタイムライブラリを使用するように1つのファイルをコンパイルし、別のファイル (たとえば、debug と retail) を使用してそのファイルをリンクしようとした場合、この警告が表示されます。 すべてのソースファイルをコンパイルして、同じランタイムライブラリを使用する必要があります。 詳細については、「 [/md、/mt、/ld (ランタイムライブラリを使用する)](../../build/reference/md-mt-ld-use-run-time-library.md)コンパイラオプション」を参照してください。

リンカーの[/verbose: LIB](../../build/reference/verbose-print-progress-messages.md)スイッチを使用して、リンカーが検索するライブラリを調べることができます。 たとえば、実行可能ファイルでマルチスレッドの非デバッグランタイムライブラリを使用する場合、報告される一覧には LIBCMT.LIB が含まれている必要があり、LIBCMTD、MSVCRT.DLL、MSVCRTD.LIB は含まれません。 無視する各ライブラリに対して[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)を使用することにより、無効なランタイムライブラリを無視するようにリンカーに指示できます。

次の表は、使用するランタイムライブラリに応じてどのライブラリを無視すべきかを示しています。 コマンドラインで、ライブラリごとに1つの **/NODEFAULTLIB**オプションを使用して無視します。 Visual Studio IDE で、[**特定の既定のライブラリを無視**する] プロパティのセミコロンで、ライブラリを区別しないようにします。

| このランタイムライブラリを使用するには | これらのライブラリを無視 |
|-----------------------------------|----------------------------|
| マルチスレッド (libcmt.lib) | msvcrt.dll;libcmtd .lib;msvcrtd.lib |
| DLL を使用したマルチスレッド (msvcrt.dll) | libcmt.lib;libcmtd .lib;msvcrtd.lib |
| マルチスレッドのデバッグ (libcmtd .lib) | libcmt.lib;msvcrt.dll;msvcrtd.lib |
| DLL を使用したマルチスレッドデバッグ (msvcrtd.lib) | libcmt.lib;msvcrt.dll;libcmtd .lib |

たとえば、この警告を受け取った場合に、ランタイムライブラリの非デバッグ DLL バージョンを使用する実行可能ファイルを作成するには、リンカーで次のオプションを使用します。

```cmd
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```
