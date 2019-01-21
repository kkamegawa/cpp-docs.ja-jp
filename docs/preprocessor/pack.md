---
title: pack
ms.date: 12/17/2018
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: 9b959c161a933cc76590cfbd65d295aad36f07d7
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627515"
---
# <a name="pack"></a>pack
構造体メンバー、共用体メンバー、およびクラス メンバーのパッキング アラインメントを指定します。

## <a name="syntax"></a>構文

```
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )
```

### <a name="parameters"></a>パラメーター

**表示します。**<br/>
(省略可能)パッキング アラインメントの現在のバイト値を表示します。 値は警告メッセージによって表示されます。

**push**<br/>
(省略可能)内部コンパイラ スタック、およびセットの現在のパッキング アラインメント値を現在のパッキング アラインメント値のプッシュ*n*します。 場合*n*が指定されていない、現在のパッキング アラインメント値がプッシュされます。

**pop**<br/>
(省略可能)内部コンパイラ スタックの上部からレコードを削除します。 場合*n*がで指定されていない**pop**スタックの上部にある結果のレコードに関連付けられているパッキング値は、新しいパッキング アラインメント値です。 場合*n*指定すると、たとえば、 `#pragma pack(pop, 16)`、 *n*が新しいパッキング アラインメント値です。 ポップすると場合*識別子*、たとえば、 `#pragma pack(pop, r1)`、スタック上のすべてのレコードがあるレコードまでポップされます。 その後*識別子*が見つかった。 このレコードがポップされ、スタックの最上位の結果のレコードに関連付けられているパッキング値が新しいパッキング アラインメント値になります。 ポップすると場合、*識別子*内、スタック上のどのレコードが見つからない、 **pop**は無視されます。

*identifier*<br/>
(省略可能)使用すると*プッシュ*、内部コンパイラ スタックのレコードに名前を割り当てます。 使用すると**pop**、レコードまで内部スタックからポップ*識別子*が削除された場合*識別子*は内部のスタックに何もポップされます。

*n*<br/>
(省略可能)パッキングの使用をバイト単位で、値を指定します。 場合、コンパイラ オプション[/Zp](../build/reference/zp-struct-member-alignment.md) 、モジュールの既定値の設定されていない*n*が 8。 有効値は 1、2、4、8、および 16 です。 メンバーのアラインメントはいずれかである境界上の倍数である*n*またはのメンバーのサイズの倍数で小さい方です。

`#pragma pack(pop, identifier, n)` 定義されていません。

## <a name="remarks"></a>Remarks

クラスをパッキングすると、そのメンバーはメモリ内で互いの直後に配置されます。そのため、一部またはすべてのメンバーがターゲット アーキテクチャの既定のアラインメントより小さい境界内にアラインされる場合があります。 **パック**データ宣言レベルで制御します。 これに対しコンパイラ オプションから[/Zp](../build/reference/zp-struct-member-alignment.md)、モジュール レベルの制御のみを提供します。 **パック**は 1 つ目の反映**構造体**、**共用体**、または**クラス**プラグマが発生した後に宣言します。 **パック**定義に影響を与えません。 呼び出す**パック**引数セットなしで*n*コンパイラ オプションで設定された値に`/Zp`します。 コンパイラ オプションを設定しない場合、既定値は 8 になります。

構造体の配置を変更すると、メモリの領域はそれほど使用されていなくても、パフォーマンスが低下したり、アラインメントされていないアクセスについてハードウェアで生成された例外を受け取る場合があります。  この例外の動作を変更するを使用[SetErrorMode](https://msdn.microsoft.com/library/windows/desktop/ms680621)します。

アラインメントの変更方法の詳細については、次のトピックを参照してください。

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [構造体の配置例](../build/x64-software-conventions.md#examples-of-structure-alignment)(x64 固有)

   > [!WARNING]
   > Visual Studio 2015 以降では、標準の alignas および alignof 演算子を使用できることに注意してください。これらは `__alignof` および `declspec( align )` とは異なり、コンパイラ間で移植できます。 C++ 標準は扱いません梱包、使用する必要がありますので**パック**(または他のコンパイラで対応する拡張機能) をターゲット アーキテクチャのワード サイズより小さいアラインメントを指定します。

## <a name="examples"></a>使用例

次の例は、使用する方法を示します、**パック**プラグマ構造体のアラインメントを変更します。

```cpp
// pragma_directives_pack.cpp
#include <stddef.h>
#include <stdio.h>

struct S {
   int i;   // size 4
   short j;   // size 2
   double k;   // size 8
};

#pragma pack(2)
struct T {
   int i;
   short j;
   double k;
};

int main() {
   printf("%zu ", offsetof(S, i));
   printf("%zu ", offsetof(S, j));
   printf("%zu\n", offsetof(S, k));

   printf("%zu ", offsetof(T, i));
   printf("%zu ", offsetof(T, j));
   printf("%zu\n", offsetof(T, k));
}
```

```Output
0 4 8
0 4 6
```

次の例は、使用する方法を示します、*プッシュ*、 *pop*、および*表示*構文。

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>関連項目

[プラグマ ディレクティブと __Pragma キーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)