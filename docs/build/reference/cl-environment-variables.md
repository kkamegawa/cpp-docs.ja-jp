---
title: 環境変数 CL
ms.date: 06/06/2019
f1_keywords:
- cl
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 0f7930728ef1bf6bea50c4388d52d30c569a8795
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821537"
---
# <a name="cl-environment-variables"></a>環境変数 CL

CL ツールでは、次の環境変数を使用します。

- CL と\_CL_、定義されている場合。 定義されている引数および CL ツールは、オプションとコマンドラインの引数を環境変数 CL で定義されている引数の前に付加し、オプションを追加します\_CL_、処理する前にします。

- Visual Studio のインストールの \include サブディレクトリをポイントする必要がありますが含まれます。

- LIBPATH を参照するメタデータ ファイルを検索するディレクトリを指定する[#using](../../preprocessor/hash-using-directive-cpp.md)します。 LIBPATH の詳細については、次を参照してください。 [#using](../../preprocessor/hash-using-directive-cpp.md)します。

CL を設定することができますまたは\_CL_ 環境変数を次の構文を使用します。

> SET CL=[ [*option*] ... [*file*] ...] [/link *link-opt* ...] \
> SET \_CL\_=[ [*option*] ... [*file*] ...] [/link *link-opt* ...]

詳細については、CL の引数に対してと\_CL_ 環境変数を参照してください[MSVC コンパイラのコマンドライン構文](compiler-command-line-syntax.md)します。

これらの環境変数を使用すると、ファイルおよび最も頻繁に使用するオプションを定義します。 コマンドラインを使用して、CL に特定の目的のファイルおよびオプションの詳細を提供します。 CL と\_CL_ 環境変数は 1024 文字 (コマンドライン入力の制限) に制限されています。

使用することはできません、 [/D](d-preprocessor-definitions.md)等号 (=) を使用するシンボルを定義するオプション ( **=** )。 代わりに、シャープ記号を使用することができます ( **#** ) の等号 (=)。 この方法では、CL を使用することができますまたは\_CL_ の環境変数の明示的な値を持つプリプロセッサ定数を定義する — たとえば、`/DDEBUG#1`を定義する`DEBUG=1`。

関連情報については、次を参照してください。[環境変数を設定](../setting-the-path-and-environment-variables-for-command-line-builds.md)します。

## <a name="examples"></a>使用例

次のコマンドは、環境変数 CL を設定する例を示します。

> SET CL=/Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ

環境変数 CL 設定されている場合、入力した場合`CL INPUT.C`コマンドラインでコマンドを有効になります。

> CL /Zp2 /Ox /I\INCLUDE\MYINCLS \LIB\BINMODE.OBJ INPUT.C

次の例では、単純な CL コマンドを実行すると、FILE1.c および FILE2.c の各ソース ファイルがコンパイルされ、FILE1.obj、FILE2.obj、および FILE3.obj の各オブジェクト ファイルがリンクされます。

> SET CL=FILE1.C FILE2.C \
> SET \_CL_=FILE3.OBJ \
> CL

これらの環境変数では、次のコマンドラインと同じ効果がある CL への呼び出しを行います。

> CL FILE1.C FILE2.C FILE3.OBJ

## <a name="see-also"></a>関連項目

[コンパイラ オプションの設定](compiler-command-line-syntax.md) \
[MSVC コンパイラ オプション](compiler-options.md)
