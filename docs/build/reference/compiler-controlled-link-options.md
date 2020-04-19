---
title: Compiler-Controlled LINK Options
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: bc7a6cc596f138daa373042abca51642c24cf737
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342864"
---
# <a name="compiler-controlled-link-options"></a>Compiler-Controlled LINK Options

CL コンパイラは、/c オプションを指定しない限り、リンクを自動的に呼び出します。 CL は、いくつかのコマンド ライン オプションと引数をリンカーに制御を提供します。 次の表では、リンクに影響を与える CL の機能をまとめたものです。

|CL の仕様|CL アクション リンクに影響を与える|
|----------------------|---------------------------------|
|.C、.cxx、.cpp、または .def 以外の任意のファイル名拡張子|リンクへの入力としてファイル名を渡します|
|*ファイル名*.def|/DEF を渡します*filename*.def。|
|/F*数*|パス/STACK:*数*|
|/Fd*ファイル名*|/PDB を渡します*ファイル名。*|
|/Fe*ファイル名*|渡します/アウト:*ファイル名*|
|/Fm*ファイル名*|パス/MAP:*ファイル名*|
|/Gy|パッケージ化された関数 (Comdat); を作成します。関数レベルのリンクを可能に|
|/LD|/DLL を渡します|
|/LDd|/DLL を渡します|
|/link|コマンドラインの残りの部分を LINK に渡します。|
|/MD、/MT または|既定のライブラリ名を .obj ファイル配置します。|
|/Mdd または/MTd|既定のライブラリ名は、.obj ファイルに配置します。 シンボルを定義 **_DEBUG**|
|/nologo|/NOLOGO を渡します|
|/Zd|/DEBUG のパス|
|/Zi または/Z7|/DEBUG のパス|
|/Zl|.Obj ファイルから既定のライブラリ名を省略します。|

詳細については、次を参照してください。 [MSVC コンパイラ オプション](compiler-options.md)します。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
