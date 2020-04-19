---
title: include_alias プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
ms.openlocfilehash: aa3714186e8f95d4044ba5a3b2bc2d5fcfb1fc9c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218905"
---
# <a name="include_alias-pragma"></a>include_alias プラグマ

`#include`ディレクティブで*alias_filename*が見つかった場合に、コンパイラによって*actual_filename*が代わりに置換されることを指定します。

## <a name="syntax"></a>構文

<!-- localization note - it's important to have the italic and bold characters immediately adjacent here. -->
> **#pragma include_alias (** "*alias_filename*" **,** "*actual_filename*" **)** \
> **#pragma include_alias (** \< *alias_filename*>  **、** *actual_filename*) \<> 

## <a name="remarks"></a>Remarks

**Include_alias** pragma ディレクティブを使用すると、ソースファイルに含まれるファイル名に対して異なる名前またはパスを持つファイルを置き換えることができます。 たとえば、ファイルシステムによっては、8.3 FAT ファイルシステムの制限よりも長いヘッダーファイル名が許可されている場合があります。 長い方のヘッダーファイル名の最初の8文字が一意でない可能性があるため、コンパイラは長い名前を8.3 に切り捨てるだけではありません。 コンパイラは、 `#include`ディレクティブ内で*alias_filename*文字列を認識するたびに、代わりに名前*actual_filename*を置き換えます。 次に、 *actual_filename*ヘッダーファイルを読み込みます。 このプラグマは、対応する `#include` ディレクティブよりも前に記述する必要があります。 例えば:

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

検索するエイリアスは、仕様と正確に一致している必要があります。 大文字と小文字、スペル、二重引用符や山かっこの使用はすべて一致している必要があります。 **Include_alias**プラグマは、ファイル名に対して単純な文字列照合を行います。 他のファイル名の検証は実行されません。 たとえば、次のようなディレクティブがあるとします。

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

ヘッダーファイルの文字列が正確に一致しないため、別名の置換は行われません。 また、および`/Yu` `/Yc`コンパイラオプションの引数として使用されるヘッダーファイル名、またはプラグマは置き換えられません。`hdrstop` たとえば、ソース ファイルに次のディレクティブが含まれている場合、

```cpp
#include <AppleSystemHeaderStop.h>
```

対応するコンパイラ オプションは、次のようになります。

> **/YcAppleSystemHeaderStop.h**

**Include_alias**プラグマを使用して、任意のヘッダーファイル名を別のファイル名にマップできます。 例えば:

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

二重引用符で囲まれたファイル名と、山かっこで囲まれたファイル名を混在させないでください。 たとえば、上記の2つ`#pragma include_alias`のディレクティブを指定した場合、コンパイラは次`#include`のディレクティブを置き換えません。

```cpp
#include <api.h>
#include "stdio.h"
```

さらに、次のディレクティブはエラーになります。

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

エラーメッセージまたは定義済み`__FILE__`マクロの値として報告されたファイル名は、置換が実行された後のファイル名です。 たとえば、次のディレクティブの後の出力を参照してください。

```cpp
#pragma include_alias( "VERYLONGFILENAME.H", "myfile.h" )
#include "VERYLONGFILENAME.H"
```

非常に*長いファイル名にエラーがあります。H*では、次のエラーメッセージが生成されます。

```Output
myfile.h(15) : error C2059 : syntax error
```

また、推移性はサポートされていないことに注意してください。 次のようなディレクティブがあるとします。

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

コンパイラは、 *3 .h*ではなく、 *2 つの .h*ファイルを検索します。

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
