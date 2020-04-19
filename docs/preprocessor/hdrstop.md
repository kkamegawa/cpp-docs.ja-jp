---
title: hdrstop プラグマ
ms.date: 08/29/2019
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
ms.openlocfilehash: f540f0f01fe654213af15afa8fbf5cbd94e4b7e2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221023"
---
# <a name="hdrstop-pragma"></a>hdrstop プラグマ

プリコンパイルファイル名、およびコンパイル状態が保存されている場所に対する追加の制御を提供します。

## <a name="syntax"></a>構文

> **#pragma hdrstop**[("*ファイル名*")]

## <a name="remarks"></a>Remarks

*Filename*は、使用または作成するプリコンパイル済みヘッダーファイルの名前です ( [/Yu](../build/reference/yu-use-precompiled-header-file.md)または[/yc](../build/reference/yc-create-precompiled-header-file.md)が指定されているかどうかによって異なります)。 *Filename*にパスの指定が含まれていない場合、プリコンパイル済みヘッダーファイルはソースファイルと同じディレクトリに存在すると見なされます。

をC++ 指定してコンパイルしたときに、Cまたはファイルにhdrstopプラグマが含まれている場合、コンパイラは、プラグマの位置までコンパイルの状態を保存し`/Yc`ます。 プラグマの後に続くコードのコンパイル済みの状態は保存されません。

コンパイル済みの状態を保存するプリコンパイル済みヘッダーファイルの名前を指定するには、 *filename*を使用します。 **Hdrstop**と*filename*の間のスペースは省略可能です。 **Hdrstop**プラグマで指定されたファイル名は文字列であるため、C またはC++文字列の制約が適用されます。 具体的には、文字列を引用符で囲み、エスケープ文字 (円記号) を使用してディレクトリ名を指定する必要があります。 例えば:

```C
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

プリコンパイル済みヘッダー ファイルの名前は、次の規則 (優先度順に表示) に従って決定されます。

1. `/Fp`コンパイラオプションの引数

2. の*filename*引数`#pragma hdrstop`

3. 拡張子 .PCH を持つソース ファイルのベース名

`/Yc`オプションと`/Yu`オプションについて、2つのコンパイルオプションと**hdrstop**プラグマのどちらもファイル名を指定しない場合、ソースファイルの基本名がプリコンパイル済みヘッダーファイルのベース名として使用されます。

また、次のように、プリプロセス コマンドを使用してマクロ置換を実行することもできます。

```C
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

**Hdrstop**プラグマを配置できる場所は、次の規則によって決まります。

- すべてのデータ宣言、関数宣言、および定義の外にある必要があります。

- ヘッダー ファイルにではなく、ソース ファイルに指定する必要があります。

## <a name="example"></a>例

```C
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    // ...                           // Some code to display string
}
#pragma hdrstop
```

この例では、2つのファイルが含まれ、インライン関数が定義された後に**hdrstop**プラグマが表示されます。 この場所は、最初はプラグマの位置が奇数であるように見えます。 ただし、手動プリコンパイルオプション`/Yc`を使用すると、および`/Yu`を**hdrstop**プラグマと共に使用することで、インラインコードでもソースファイル全体をプリコンパイルできることを考慮してください。 Microsoft コンパイラでは、データ宣言以外のプリコンパイルも実行できます。

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
