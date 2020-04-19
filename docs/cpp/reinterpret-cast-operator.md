---
title: reinterpret_cast 演算子
ms.date: 11/04/2016
f1_keywords:
- reinterpret_cast_cpp
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
ms.openlocfilehash: 421a1fdce6834f800cd33a55d75c9dc4f88ffc93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403426"
---
# <a name="reinterpret_cast-operator"></a>reinterpret_cast 演算子

ポインターが他のポインター型に変換されることを許可します。 また、整数型から任意のポインター型への変換およびその逆の変換を許可します。

## <a name="syntax"></a>構文

```
reinterpret_cast < type-id > ( expression )
```

## <a name="remarks"></a>Remarks

不正使用、 **reinterpret_cast**演算子は簡単に安全でないあります。 必要な変換が本質的に低レベルでない限り、他のキャスト演算子の 1 つを使用する必要があります。

**Reinterpret_cast**演算子はなどの変換を使用できます`char*`に`int*`、または`One_class*`に`Unrelated_class*`、これは本質的に安全ではありません。

結果、 **reinterpret_cast**元の型にキャストされている以外は安全に使用することはできません。 その他の使用方法は、最高でも非ポータブルです。

**reinterpret_cast**演算子はキャストできません、 **const**、**volatile**、または **_ _unaligned**属性。 参照してください[const_cast 演算子](../cpp/const-cast-operator.md)については、これらの属性を削除します。

**Reinterpret_cast**演算子は、null ポインターの値を変換先の型の null ポインター値に変換します。

実用的用途の 1 つ**reinterpret_cast**はハッシュ関数で、その 2 つの異なる方法でインデックスに値を割り当てる値ほとんどエンドを同じインデックスを持つ。

```cpp
#include <iostream>
using namespace std;

// Returns a hash code based on an address
unsigned short Hash( void *p ) {
   unsigned int val = reinterpret_cast<unsigned int>( p );
   return ( unsigned short )( val ^ (val >> 16));
}

using namespace std;
int main() {
   int a[20];
   for ( int i = 0; i < 20; i++ )
      cout << Hash( a + i ) << endl;
}

Output:
64641
64645
64889
64893
64881
64885
64873
64877
64865
64869
64857
64861
64849
64853
64841
64845
64833
64837
64825
64829
```

**Reinterpret_cast**により、整数型として扱うへのポインター。 結果は、一意のインデックス (高レベルの発生確率で一意) を生成するためにビット シフトされ、XOR されます。 インデックスは、関数の戻り値の型への標準 C 形式のキャストにより切り捨てられます。

## <a name="see-also"></a>関連項目

[キャスト演算子](../cpp/casting-operators.md)<br/>
[キーワード](../cpp/keywords-cpp.md)