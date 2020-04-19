---
title: sizeof 演算子
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: 9edd6420193fbc1ff6013c545b294851ce105848
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267220"
---
# <a name="sizeof-operator"></a>sizeof 演算子

型のサイズに対するオペランドのサイズが得られます**char**します。

> [!NOTE]
>  については、`sizeof ...`演算子を参照してください[楕円および可変個引数テンプレート](../cpp/ellipses-and-variadic-templates.md)します。

## <a name="syntax"></a>構文

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Remarks

結果、 **sizeof**演算子`size_t`、インクルード ファイルで定義されている整数型\<stddef.h >。 この演算子を使うと、コンピューターに依存するデータ サイズをプログラムで指定せずに済みます。

オペランド**sizeof**次のいずれかを指定できます。

- 型の名前。 使用する**sizeof**型の名前を持つ名前をかっこで囲む必要があります。

- 任意の式を指定します。 式を使用すると**sizeof**またはかっこがない場合に指定することができます。 式は評価されません。

ときに、 **sizeof**演算子は型のオブジェクトに適用**char**1 になります。 ときに、 **sizeof**演算子が配列に適用される場合、配列識別子によって表されるポインターのサイズではなく、その配列内のバイトの合計数になります。 配列識別子によって表されるポインターのサイズを取得することをパラメーターとして渡す関数を使用する**sizeof**します。 例:

## <a name="example"></a>例

```cpp
#include <iostream>
using namespace std;

size_t getPtrSize( char *ptr )
{
   return sizeof( ptr );
}

int main()
{
   char szHello[] = "Hello, world!";

   cout  << "The size of a char is: "
         << sizeof( char )
         << "\nThe length of " << szHello << " is: "
         << sizeof szHello
         << "\nThe size of the pointer is "
         << getPtrSize( szHello ) << endl;
}
```

## <a name="sample-output"></a>出力例

```Output
The size of a char is: 1
The length of Hello, world! is: 14
The size of the pointer is 4
```

ときに、 **sizeof**演算子に適用されます、**class**、**struct**、または**union**型、結果は、そのオブジェクト内のバイトの数単語の境界にメンバーをアラインする追加の埋め込みと入力します。 結果は、個々のメンバーのストレージ要件を追加することで計算されたサイズには必ずしも対応しません。 [/Zp](../build/reference/zp-struct-member-alignment.md)コンパイラ オプションおよび[パック](../preprocessor/pack.md)プラグマは、メンバーのアラインメント境界に影響します。

**Sizeof**演算子は空のクラスの場合でも、0 を生成することはありません。

**Sizeof**演算子は、次のオペランドでは使用できません。

- 関数 (ただし、 **sizeof**関数へのポインターに適用できます)。

- ビット フィールド。

- 定義されていないクラス。

- 型**void**します。

- 動的に割り当てられる配列。

- 外部配列。

- 不完全な型。

- かっこで囲まれた不完全な型の名前。

ときに、 **sizeof**演算子は参照に適用、結果は、同じまるで**sizeof**オブジェクト自体に適用されている必要があります。

可変長配列が構造体の最後の要素の場合、 **sizeof**演算子は配列のない構造体のサイズを返します。

**Sizeof**形式の式を使用して、配列内の要素の数を計算する演算子が使用される多くの場合。

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>関連項目

[単項演算子を含む式](../cpp/expressions-with-unary-operators.md)<br/>
[キーワード](../cpp/keywords-cpp.md)