---
title: プリコンパイル済みヘッダー ファイル
ms.date: 10/24/2019
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- cl.exe compiler, precompiling code
- .pch files, creating
ms.assetid: e2cdb404-a517-4189-9771-c869c660cb1b
ms.openlocfilehash: 071839df431071a7d8921d1b445094f886ad38e2
ms.sourcegitcommit: 33a898bf976c65f998b4e88a84765a0cef4193a8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920105"
---
# <a name="precompiled-header-files"></a>プリコンパイル済みヘッダー ファイル

Visual Studio で新しいプロジェクトを作成すると、 *pch*という名前の*プリコンパイル済みヘッダーファイル*がプロジェクトに追加されます。 (Visual Studio 2017 以前では、ファイルは*stdafx.h*と呼ばれていました)。ファイルの目的は、ビルドプロセスを高速化することです。 `<vector>`などの標準ライブラリヘッダーなど、安定したヘッダーファイルをここに含めます。 プリコンパイル済みヘッダーは、それが含まれている場合、またはそれに含まれるファイルが変更された場合にのみコンパイルされます。 プロジェクトのソースコードでのみ変更を加えた場合、プリコンパイル済みヘッダーのコンパイルはスキップされます。 

プリコンパイル済みヘッダーのコンパイラオプションは、 [/y](reference/y-precompiled-headers.md)です。 プロジェクトのプロパティページでは、オプションは **構成プロパティ の > CC++ /> プリコンパイル済みヘッダー** の下にあります。 プリコンパイル済みヘッダーを使用しないように選択することも、ヘッダーファイル名と出力ファイルの名前とパスを指定することもできます。 

## <a name="custom-precompiled-code"></a>カスタムプリコンパイル済みコード

ビルドに長時間かかる大規模なプロジェクトの場合は、カスタムプリコンパイル済みファイルの作成を検討することをお勧めします。 Microsoft C および C++ コンパイラは、インライン コードを含む、C または C++ コードをプリコンパイルするためのオプションを提供します。 このパフォーマンス機能を使用して、安定したコードの本体をコンパイルし、ファイル内のコードのコンパイル済みの状態を格納します。さらに、後続のコンパイル中に、プリコンパイルされたコードと開発中のコードを結合できます。 安定したコードは再コンパイルする必要がないので、後続のコンパイルが高速化します。

## <a name="when-to-precompile-source-code"></a>ソース コードをプリコンパイルする時期

プリコンパイルされたコードは、コンパイル時間を短縮するために開発サイクル中に役立ちます。特に次の場合に役立ちます。

- 頻繁に変更される大きなコード本文を常に使用します。

- プログラムは複数のモジュールで構成されています。これらのモジュールはすべて、インクルードファイルの標準セットと同じコンパイルオプションを使用します。 この場合、すべてのインクルードファイルをプリコンパイル済みヘッダーにプリコンパイルできます。

最初のコンパイル (プリコンパイル済みヘッダー (PCH) ファイルを作成するコンパイル) は、後続のコンパイルよりも少し時間がかかります。 後続のコンパイルは、プリコンパイル済みコードを含めることにより、より迅速に進めることができます。

C とC++プログラムの両方をプリコンパイルできます。 プログラミングC++では、クラスインターフェイス情報をヘッダーファイルに分割するのが一般的です。 これらのヘッダーファイルは、後でクラスを使用するプログラムに含めることができます。 これらのヘッダーをプリコンパイルすることにより、プログラムがコンパイルされるまでにかかる時間を短縮できます。

> [!NOTE]
> ソースファイルごとに使用できるプリコンパイル済みヘッダー (.pch) ファイルは1つだけですが、プロジェクトでは複数の .pch ファイルを使用できます。

## <a name="two-choices-for-precompiling-code"></a>コードをプリコンパイルする 2 つの方法

C またはC++コードをプリコンパイルできます。ヘッダーファイルのみをプリコンパイルすることはできません。

プリコンパイルを行うには計画を立てる必要がありますが、単純なヘッダーファイル以外のソースコードをプリコンパイルすると、コンパイルが大幅に高速化されます。

ソースファイルでヘッダーファイルの共通セットが使用されていることがわかっているが、同じ順序でインクルードされていない、またはプリコンパイルにソースコードを含める必要がある場合は、コードをプリコンパイルします。

プリコンパイル済みヘッダーのオプションは、 [/yc (プリコンパイル済みヘッダーファイルの作成)](reference/yc-create-precompiled-header-file.md)および[/Yu (プリコンパイル済みヘッダーファイルの使用)](reference/yu-use-precompiled-header-file.md)です。 **/Yc**を使用してプリコンパイル済みヘッダーを作成します。 **/Yc**をオプションの[hdrstop](../preprocessor/hdrstop.md)プラグマと共に使用すると、ヘッダーファイルとソースコードの両方をプリコンパイルできます。 既存のコンパイルで既存のプリコンパイル済みヘッダーを使用するには、 **[/yu]** を選択します。 **/Fp**を **/Yc**オプションと **/yu**オプションと共に使用して、プリコンパイル済みヘッダーの代替名を指定することもできます。

**/Yu**と **/yc**に関するコンパイラオプションのリファレンストピックでは、開発環境でこの機能にアクセスする方法について説明します。

## <a name="precompiled-header-consistency-rules"></a>プリコンパイル済みヘッダーの一貫性規則

PCH ファイルには、コンピューター環境に関する情報とプログラムに関するメモリアドレス情報が含まれているため、PCH ファイルを作成したコンピューター上でのみ使用してください。

## <a name="consistency-rules-for-per-file-use-of-precompiled-headers"></a>PCH ファイルの使用時の一貫性規則

[/Yu](reference/yu-use-precompiled-header-file.md)コンパイラオプションを使用すると、使用する PCH ファイルを指定できます。

PCH ファイルを使用する場合、コンパイラは、PCH ファイルを作成したときに有効であったものと同じコンパイル環境を想定しています。ただし、それ以外の場合はを指定する必要があります。 コンパイラが不整合を検出した場合は、警告を発行し、可能な場合は不整合を識別します。 このような警告は、必ずしも PCH ファイルに問題があることを示しているわけではありません。発生する可能性がある競合を警告するだけです。 PCH ファイルの一貫性の要件については、次のセクションで説明します。

### <a name="compiler-option-consistency"></a>コンパイラオプションの一貫性

PCH ファイルを使用すると、次のコンパイラオプションで不整合の警告が発生する可能性があります。

- プリプロセッサ (/D) オプションを使用して作成されたマクロは、PCH ファイルを作成したコンパイルと現在のコンパイルの間で同じである必要があります。 定義された定数の状態はチェックされませんが、これらの変更が発生すると、予測できない結果が発生する可能性があります。

- PCH ファイルは、/E オプションと/EP オプションでは機能しません。

- Pch ファイルを使用する後続のコンパイルでこれらのオプションを使用できるようにするには、[参照情報の生成] (/FR) オプションまたは [ローカル変数の除外] オプション (/Fr) を使用して PCH ファイルを作成する必要があります。

### <a name="c-70-compatible-z7"></a>C 7.0 互換 (/Z7)

PCH ファイルの作成時にこのオプションが有効になっている場合、PCH ファイルを使用する後続のコンパイルでは、デバッグ情報を使用できます。

PCH ファイルの作成時に、C 7.0 互換 (/Z7) オプションが有効になっていない場合、PCH ファイルと/Z7 を使用する後続のコンパイルで警告がトリガーされます。 デバッグ情報は現在の .obj ファイルに配置されます。 PCH ファイルで定義されているローカルシンボルは、デバッガーでは使用できません。

### <a name="include-path-consistency"></a>パスの一貫性を含める

PCH ファイルには、作成時に有効だったインクルードパスに関する情報は含まれていません。 PCH ファイルを使用する場合、コンパイラは常に現在のコンパイルで指定されたインクルードパスを使用します。

### <a name="source-file-consistency"></a>ソースファイルの整合性

[プリコンパイル済みヘッダーファイル (/Yu) を使用する] オプションを指定すると、コンパイラは、プリコンパイルされるソースコードに表示されるすべてのプリプロセッサディレクティブ (プラグマを含む) を無視します。 このようなプリプロセッサディレクティブによって指定されるコンパイルは、[プリコンパイル済みヘッダーファイルの作成] オプションで使用されるコンパイルと同じである必要があります。

### <a name="pragma-consistency"></a>プラグマの一貫性

PCH ファイルの作成中に処理されるプラグマは、通常、PCH ファイルが使用されるファイルに影響します。 `comment` と `message` のプラグマは、コンパイルの残りの部分には影響しません。

これらのプラグマは、PCH ファイル内のコードにのみ影響します。これらは、その後 PCH ファイルを使用するコードには影響しません。

||||
|-|-|-|
|`comment`|`page`|`subtitle`|
|`linesize`|`pagesize`|`title`|
|`message`|`skip`||

これらのプラグマはプリコンパイル済みヘッダーの一部として保持され、プリコンパイル済みヘッダーを使用する残りのコンパイルに影響します。

||||
|-|-|-|
|`alloc_text`|`include_alias`|`pack`|
|`auto_inline`|`init_seg`|`pointers_to_members`|
|`check_stack`|`inline_depth`|`setlocale`|
|`code_seg`|`inline_recursion`|`vtordisp`|
|`data_seg`|`intrinsic`|`warning`|
|`function`|`optimize`||

## <a name="consistency-rules-for-yc-and-yu"></a>/Yc および /Yu の一貫性規則

/Yc または/Yu を使用して作成されたプリコンパイル済みヘッダーを使用すると、コンパイラは、現在のコンパイル環境と PCH ファイルを作成したときに存在していたものとを比較します。 現在のコンパイルでは、(一貫性のあるコンパイラオプション、プラグマなどを使用して) 前の環境と整合性のある環境を指定してください。 コンパイラが不整合を検出した場合は、警告を発行し、可能な場合は不整合を識別します。 このような警告は、必ずしも PCH ファイルに問題があることを示しているわけではありません。発生する可能性がある競合を警告するだけです。 以下のセクションでは、プリコンパイル済みヘッダーの一貫性の要件について説明します。

### <a name="compiler-option-consistency"></a>コンパイラオプションの一貫性

次の表に、プリコンパイル済みヘッダーを使用するときに不整合の警告が発生する可能性のあるコンパイラオプションを示します。

|オプション|名|規則|
|------------|----------|----------|
|/D|定数とマクロを定義する|プリコンパイル済みヘッダーを作成したコンパイルと現在のコンパイルの間で同じである必要があります。 定義された定数の状態はチェックされませんが、ファイルが変更された定数の値に依存している場合は、予測できない結果が発生する可能性があります。|
|/E または/EP|プリプロセッサ出力を標準出力にコピーする|プリコンパイル済みヘッダーは、/E または/EP オプションでは機能しません。|
|/Fr または/FR|Microsoft ソースブラウザー情報の生成|/Fr オプションと/FR オプションを/Yu オプションと共に有効にするには、プリコンパイル済みヘッダーが作成されたときにも有効になっている必要があります。 プリコンパイル済みヘッダーを使用する後続のコンパイルでは、ソースブラウザー情報も生成されます。 ブラウザー情報は1つの .sbr ファイルに配置され、CodeView 情報と同じ方法で他のファイルから参照されます。 ソースブラウザー情報の配置を上書きすることはできません。|
|/GA、/GD、/GE、/Gw、または/GW|Windows プロトコルのオプション|プリコンパイル済みヘッダーを作成したコンパイルと現在のコンパイルの間で同じである必要があります。 これらのオプションが異なる場合、警告メッセージが表示します。|
|/Zi|完全なデバッグ情報の生成|プリコンパイル済みヘッダーを作成するときにこのオプションを有効にした場合、プリコンパイルを使用する後続のコンパイルでそのデバッグ情報を使用できます。 プリコンパイル済みヘッダーの作成時に/Zi が有効になっていない場合、プリコンパイルおよび/Zi オプションを使用する後続のコンパイルで警告がトリガーされます。 デバッグ情報は現在のオブジェクトファイルに配置されており、プリコンパイル済みヘッダーに定義されているローカルシンボルはデバッガーで使用できません。|

> [!NOTE]
>  プリコンパイル済みヘッダー機能は、C およびC++ソースファイルでのみ使用することを目的としています。

## <a name="using-precompiled-headers-in-a-project"></a>プロジェクトでのプリコンパイル済みヘッダーの使用

前のセクションでは、プリコンパイル済みヘッダーの概要について説明します。/Yc と/Yu、/Fp オプション、および[hdrstop](../preprocessor/hdrstop.md)プラグマです。 このセクションでは、プロジェクトで手動プリコンパイル済みヘッダーのオプションを使用する方法について説明します。これは、サンプルのメイクファイルとそれが管理するコードで終わります。

プロジェクトで手動プリコンパイル済みヘッダーオプションを使用する別の方法については、Visual Studio の既定のセットアップ時に作成された MFC/SRC ディレクトリにあるいずれかのメイクファイルを調べてください。 これらのメイクファイルは、このセクションで紹介したものと同様のアプローチを採用していますが、Microsoft Program Maintenance Utility (NMAKE) マクロをより活用し、ビルドプロセスをより細かく制御できます。

## <a name="pch-files-in-the-build-process"></a>ビルド プロセスでの PCH ファイル

ソフトウェアプロジェクトのコードベースは、通常、複数の C またはC++ソースファイル、オブジェクトファイル、ライブラリ、およびヘッダーファイルに含まれています。 通常、メイクファイルは、これらの要素の組み合わせを実行可能ファイルに調整します。 プリコンパイル済みヘッダーファイルを使用するメイクファイルの構造を次の図に示します。 この図の NMAKE マクロ名とファイル名は、「 [pch のサンプルメイクファイル](#sample-makefile-for-pch)」に記載されているコード例と同じです。また、 [Pch のコード例](#example-code-for-pch)を参照してください。

この図は、3つの図式デバイスを使用して、ビルドプロセスのフローを示しています。 名前付き四角形は、各ファイルまたはマクロを表します。3つのマクロは、1つ以上のファイルを表します。 網掛け領域は、各コンパイルまたはリンクアクションを表します。 矢印は、コンパイルまたはリンクプロセス中に結合されるファイルとマクロを示します。

![プリコンパイル済みヘッダーファイルを使用するメイクファイルの構造](media/vc30ow1.gif "プリコンパイル済みヘッダーファイルを使用するメイクファイルの構造") <br/>
プリコンパイル済みヘッダー ファイルを使用するメイクファイルの構造

図の先頭から、STABLEHDRS と BOUNDRY の両方が NMAKE マクロであり、再コンパイルが必要と思わないファイルが一覧表示されます。 これらのファイルは、コマンド文字列によってコンパイルされます。

`CL /c /W3 /Yc$(BOUNDRY) applib.cpp myapp.cpp`

プリコンパイル済みヘッダーファイル (安定した .pch) が存在しない場合、または2つのマクロに示されているファイルに変更を加えた場合のみ。 どちらの場合も、プリコンパイル済みヘッダーファイルには、STABLEHDRS マクロに示されているファイルからのコードのみが含まれます。 BOUNDRY マクロでプリコンパイルする最後のファイルを一覧表示します。

これらのマクロに表示されるファイルは、ヘッダーファイルまたは C C++またはソースファイルのいずれかになります。 (1 つの PCH ファイルは、C とC++モジュールの両方で使用することはできません)。**Hdrstop**マクロを使用して、BOUNDRY ファイル内のある時点でプリコンパイルを停止することができます。 詳細については、 [hdrstop](../preprocessor/hdrstop.md)を参照してください。

図を続行すると、最後のアプリケーションで使用されているサポートコードがによって表されます。 これは、UNSTABLEHDRS マクロに示されているファイルと、プリコンパイル済みヘッダーのプリコンパイル済みコードから作成されます。

MYAPP は、最終的なアプリケーションを表します。 これは、MYAPP、UNSTABLEHDRS マクロに示されているファイル、およびプリコンパイル済みヘッダーのプリコンパイル済みコードから作成されます。

最後に、実行可能ファイル (MYAPP) を実行します。EXE) を作成するには、OBJ マクロに一覧表示されているファイルをリンクします。

## <a name="sample-makefile-for-pch"></a>PCH のサンプル メイクファイル

次のメイクファイルは、マクロとを使用します。もし！それ以外の場合は!ENDIF プロジェクトへの適応を簡略化するための、制御フロー制御コマンドの構造。

```NMAKE
# Makefile : Illustrates the effective use of precompiled
#            headers in a project
# Usage:     NMAKE option
# option:    DEBUG=[0|1]
#            (DEBUG not defined is equivalent to DEBUG=0)
#
OBJS = myapp.obj applib.obj
# List all stable header files in the STABLEHDRS macro.
STABLEHDRS = stable.h another.h
# List the final header file to be precompiled here:
BOUNDRY = stable.h
# List header files under development here:
UNSTABLEHDRS = unstable.h
# List all compiler options common to both debug and final
# versions of your code here:
CLFLAGS = /c /W3
# List all linker options common to both debug and final
# versions of your code here:
LINKFLAGS = /nologo
!IF "$(DEBUG)" == "1"
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi
LINKFLAGS = $(LINKFLAGS) /COD
LIBS      = slibce
!ELSE
CLFLAGS   = $(CLFLAGS) /Oselg /Gs
LINKFLAGS = $(LINKFLAGS)
LIBS      = slibce
!ENDIF
myapp.exe: $(OBJS)
    link $(LINKFLAGS) @<<
$(OBJS), myapp, NUL, $(LIBS), NUL;
<<
# Compile myapp
myapp.obj  : myapp.cpp $(UNSTABLEHDRS)  stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    myapp.cpp
# Compile applib
applib.obj : applib.cpp $(UNSTABLEHDRS) stable.pch
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    applib.cpp
# Compile headers
stable.pch : $(STABLEHDRS)
    $(CPP) $(CLFLAGS) /Yc$(BOUNDRY)    applib.cpp myapp.cpp
```

[ビルドプロセスの PCH ファイル](#pch-files-in-the-build-process)で、「プリコンパイル済みヘッダーファイルを使用するメイクファイルの構造」に示されている STABLEHDRS、BOUNDRY、および UNSTABLEHDRS マクロ以外に、このメイクファイルには clflags マクロと linkflags マクロが用意されています。 これらのマクロを使用して、アプリケーションの実行可能ファイルのデバッグバージョンまたは最終バージョンをビルドするかどうかによって適用されるコンパイラオプションとリンカーオプションを一覧表示する必要があります。 また、プロジェクトに必要なライブラリを一覧表示する lib マクロもあります。

メイクファイルでも!もし！それ以外の場合は!ENDIF は、NMAKE のコマンドラインでデバッグシンボルを定義するかどうかを検出します。

```NMAKE
NMAKE DEBUG=[1|0]
```

この機能により、開発中に同じメイクファイルを使用したり、プログラムの最終バージョンを使用したりできるようになります。最終バージョンには DEBUG = 0 を使用します。 次のコマンドラインは同等です。

```NMAKE
NMAKE
NMAKE DEBUG=0
```

メイクデータの詳細については、「 [NMAKE リファレンス](reference/nmake-reference.md)」を参照してください。 「 [MSVC Compiler options](reference/compiler-options.md) 」と「 [MSVC リンカー options](reference/linker-options.md)」も参照してください。

## <a name="example-code-for-pch"></a>PCH のサンプル コード

[ビルドプロセスの Pch ファイル](#pch-files-in-the-build-process)と[Pch のサンプルメイク](#sample-makefile-for-pch)ファイルでは、次のソースファイルが使用されます。 コメントには重要な情報が含まれていることに注意してください。

```cpp
// ANOTHER.H : Contains the interface to code that is not
//             likely to change.
//
#ifndef __ANOTHER_H
#define __ANOTHER_H
#include<iostream>
void savemoretime( void );
#endif // __ANOTHER_H
```

```cpp
// STABLE.H : Contains the interface to code that is not likely
//            to change. List code that is likely to change
//            in the makefile's STABLEHDRS macro.
//
#ifndef __STABLE_H
#define __STABLE_H
#include<iostream>
void savetime( void );
#endif // __STABLE_H
```

```cpp
// UNSTABLE.H : Contains the interface to code that is
//              likely to change. As the code in a header
//              file becomes stable, remove the header file
//              from the makefile's UNSTABLEHDR macro and list
//              it in the STABLEHDRS macro.
//
#ifndef __UNSTABLE_H
#define __UNSTABLE_H
#include<iostream>
void notstable( void );
#endif // __UNSTABLE_H
```

```cpp
// APPLIB.CPP : This file contains the code that implements
//              the interface code declared in the header
//              files STABLE.H, ANOTHER.H, and UNSTABLE.H.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
using namespace std;
// The following code represents code that is deemed stable and
// not likely to change. The associated interface code is
// precompiled. In this example, the header files STABLE.H and
// ANOTHER.H are precompiled.
void savetime( void )
    { cout << "Why recompile stable code?\n"; }
void savemoretime( void )
    { cout << "Why, indeed?\n\n"; }
// The following code represents code that is still under
// development. The associated header file is not precompiled.
void notstable( void )
    { cout << "Unstable code requires"
            << " frequent recompilation.\n";
    }
```

```cpp
// MYAPP.CPP : Sample application
//             All precompiled code other than the file listed
//             in the makefile's BOUNDRY macro (stable.h in
//             this example) must be included before the file
//             listed in the BOUNDRY macro. Unstable code must
//             be included after the precompiled code.
//
#include"another.h"
#include"stable.h"
#include"unstable.h"
int main( void )
{
    savetime();
    savemoretime();
    notstable();
}
```

## <a name="see-also"></a>関連項目

[C/C++ ビルドのリファレンス](reference/c-cpp-building-reference.md)<br/>
[MSVC コンパイラ オプション](reference/compiler-options.md)
