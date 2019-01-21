---
title: include_alias
ms.date: 12/16/2018
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
ms.openlocfilehash: 9d32cad2533b6044348651797d0278bcbebcafd6
ms.sourcegitcommit: ae2f71fe0d64f1a90ef722759fe93c82abc064ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53587877"
---
# <a name="includealias"></a>include_alias

するように指定*alias_filename*で見つかりましたが、`#include`ディレクティブ、コンパイラに置換されます*actual_filename*代わりにします。

## <a name="syntax"></a>構文

> #<a name="pragma-includealiasaliasfilename-actualfilename"></a>プラグマ include_alias ("*alias_filename*「,」*actual_filename*")
> #<a name="pragma-includealiasaliasfilename-actualfilename"></a>プラグマ include_alias (\<*alias_filename*>、 \< *actual_filename*>)

## <a name="remarks"></a>Remarks

**Include_alias**プラグマ ディレクティブを使用すると、別の名前またはパスのソース ファイルが含まれているファイル名を持つファイルを置き換えてください。 たとえば、一部のファイル システムは、FAT ファイル システムの 8.3 制限よりも長いヘッダー ファイル名を許可します。 長いヘッダー ファイル名の最初の 8 文字は一意でない可能性があるため、コンパイラは、長い名前を単純に 8.3 形式に切り詰めることはできません。 たびに、コンパイラが検出されると、 *alias_filename* 、文字列を置き換える*actual_filename*、ヘッダー ファイルの検索と*actual_filename*代わりにします。 このプラグマは、対応する `#include` ディレクティブよりも前に記述する必要があります。 例:

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

検索するエイリアスは、大文字/小文字、スペル、および二重引用符や山かっこの使い方が、指定と正確に一致する必要があります。 **Include_alias**プラグマは、ファイル名に一致する単純な文字列を実行します。 その他のファイル名の検証は実行されません。 たとえば、次のようなディレクティブがあるとします。

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

ヘッダー ファイル文字列が正確に一致しないため、エイリアシング (置換) は実行されません。 引数として使用されるヘッダー ファイル名も、`/Yu`と`/Yc`コンパイラ オプション、または`hdrstop`プラグマを置き換えられません。 たとえば、ソース ファイルに次のディレクティブが含まれている場合、

```cpp
#include <AppleSystemHeaderStop.h>
```

対応するコンパイラ オプションは、次のようになります。

> /YcAppleSystemHeaderStop.h

使用することができます、 **include_alias**プラグマを任意のヘッダー ファイル名を別にマップします。 例:

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

二重引用符で囲んだファイル名と山かっこで囲んだファイル名を混同しないでください。 たとえば、前の 2 つを指定`#pragma include_alias`ディレクティブ、コンパイラでは、次を置換実行しない`#include`ディレクティブ。

```cpp
#include <api.h>
#include "stdio.h"
```

さらに、次のディレクティブはエラーになります。

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

ファイル名がエラー メッセージ、または定義済みの値として報告されることに注意してください。`__FILE__`置換が実行された後、マクロは、ファイルの名前。 たとえば、次のディレクティブの後に、出力を参照してください。

```cpp
#pragma include_alias( "VERYLONGFILENAME.H", "myfile.h" )
#include "VERYLONGFILENAME.H"
```

VERYLONGFILENAME のエラーです。H では、次のエラー メッセージが生成されます。

```Output
myfile.h(15) : error C2059 : syntax error
```

また、推移もサポートされません。 次のようなディレクティブがあるとします。

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

コンパイラは、three.h ではなく、two.h のファイルを検索します。

## <a name="see-also"></a>関連項目

[プラグマ ディレクティブと __Pragma キーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
