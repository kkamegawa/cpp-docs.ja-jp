---
title: MSVC コンパイラ コマンドラインの構文
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 5cee76d5c053dbcfef33a191dc38a958338e4a82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294344"
---
# <a name="compiler-command-line-syntax"></a>コンパイラ コマンド ラインの構文

CL のコマンド ラインでは、次の構文を使用します。

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

次の表では、CL コマンドへの入力について説明します。

|入力|説明|
|-----------|-------------|
|*オプション*|1 つまたは複数[CL オプション](compiler-options.md)します。 すべてのオプションは、すべての指定したソース ファイルに適用されるに注意してください。 オプションは、スラッシュ (/) またはダッシュ (-) のいずれかによって指定されます。 場合は、オプションは、オプションと引数の間に空白が許可されているかどうか、引数、オプションの説明のドキュメントを受け取ります。 (/HELP オプション) を除くオプション名は大文字小文字を区別します。 参照してください[CL オプションの指定順序](order-of-cl-options.md)詳細についてはします。|
|`file`|1 つまたは複数のソース ファイル、.obj ファイル、またはライブラリの名前。 CL は、ソース ファイルをコンパイルし、.obj ファイルとライブラリの名前をリンカーに渡します。 参照してください[CL ファイル名の構文](cl-filename-syntax.md)詳細についてはします。|
|*lib*|1 つまたは複数のライブラリ名。 CL は、これらの名前をリンカーに渡します。|
|*コマンド ファイル*|複数のオプションとファイル名を含むファイル。 参照してください[CL コマンド ファイル](cl-command-files.md)詳細についてはします。|
|*link-opt*|1 つまたは複数[MSVC リンカー オプション](linker-options.md)します。 CL は、これらのオプションをリンカーに渡します。|

コマンドラインでの文字数が 1024、オペレーティング システムで指定された制限を超えない限り、任意の数のオプション、ファイル名、およびライブラリの名前を指定できます。

Cl.exe の戻り値については、次を参照してください。 [cl.exe の戻り値](return-value-of-cl-exe.md)します。

> [!NOTE]
>  1024 文字の場合は、コマンド ライン入力制限は、Windows の将来のリリースでは同じままには保証されません。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)
