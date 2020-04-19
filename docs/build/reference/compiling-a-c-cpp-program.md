---
title: MSVC C と C++ コンパイラ リファレンス - Visual Studio
description: MSVC コンパイラ ツールセット オプション。
ms.date: 12/10/2018
helpviewer_keywords:
- cl.exe compiler
- cl.exe compiler, setting options
ms.assetid: f3eef5ab-d0be-4fb2-90f9-927e6ed58736
ms.openlocfilehash: 2269ba69cea2702ff190c791eb6753acb3619f7d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294149"
---
# <a name="compiling-a-cc-project"></a>C と C++ プロジェクトのコンパイル

Visual Studio IDE またはコマンドラインで、C および C++ のコンパイラ オプションを設定できます。 

## <a name="in-visual-studio"></a>Visual Studio 内

各プロジェクトのコンパイラ オプションを設定するには、Visual Studio で**プロパティ ページ** ダイアログ ボックス。 左側のウィンドウで次のように選択します。**構成プロパティ**、 **c/c++** コンパイラ オプションのカテゴリを選択するとします。 各コンパイラ オプションのトピックで、開発環境でオプションを設定する方法と、そのオプションがどこにあるかを説明します。 参照してください[MSVC コンパイラ オプション](compiler-options.md)完全な一覧についてはします。

## <a name="from-the-command-line"></a>コマンドラインから

コンパイラ (CL.exe) オプションは、次のいずれかで設定できます。

- [コマンドラインで](compiler-command-line-syntax.md)

- [コマンド ファイル](cl-command-files.md)

- [環境変数 CL](cl-environment-variables.md)

環境変数 CL で指定したオプションは、CL を起動するたびに使用されます。 環境変数 CL またはコマンド ラインでコマンド ファイルを指定すると、そのコマンド ファイルに指定されているオプションが使用されます。 コマンド ラインまたは環境変数 CL ではオプションとファイル名を 1 行しか指定できませんが、コマンド ファイルでは複数行指定できます。

コンパイラ オプションは、"左から右" に処理されます。オプションが競合する場合は、最後の、つまり一番右のオプションが優先されます。 CL とコマンド ラインが競合した場合は、コマンド ラインが優先されます。環境変数 CL の処理後にコマンド ラインが処理されるからです。

## <a name="additional-compiler-topics"></a>コンパイラに関するその他のトピック

- [MSVC コンパイラ オプション](compiler-options.md)

- [プリコンパイル済みヘッダー ファイル](../creating-precompiled-header-files.md)

- [リンカーを呼び出す CL](cl-invokes-the-linker.md)

コンパイラのホストとターゲット アーキテクチャを選択する方法については、次を参照してください。 [64 ビット、x64 ターゲットで構成する C++ プロジェクト](../configuring-programs-for-64-bit-visual-cpp.md)します。

## <a name="see-also"></a>関連項目

[C/C++ ビルドのリファレンス](c-cpp-building-reference.md)
