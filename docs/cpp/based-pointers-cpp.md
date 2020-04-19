---
title: ベース ポインター (C++)
ms.date: 10/09/2018
f1_keywords:
- __based
- _based
- __based_cpp
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
ms.openlocfilehash: 393fe8f8d12266650740942d0605152b6548d146
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857698"
---
# <a name="based-pointers-c"></a>ベース ポインター (C++)

**__Based**キーワードを使用すると、ポインター (既存のポインターからのオフセットであるポインター) に基づいてポインターを宣言できます。 **__Based**キーワードは Microsoft 固有です。

## <a name="syntax"></a>構文

```
type __based( base ) declarator
```

## <a name="remarks"></a>Remarks

ポインターアドレスに基づくポインターは、32ビットまたは64ビットのコンパイルで有効な **__based**キーワードの唯一の形式です。 Microsoft の 32 ビット C/C++ コンパイラでは、based ポインターは 32 ビットのポインター ベースからの 32 ビットのオフセットになります。 同様の制限は 64 ビット環境にもあり、based ポインターは 64 ビット ベースからの 64 ビット オフセットになります。

ポインターに基づいたポインターの使用方法の 1 つは、ポインターを含む永続的な識別子での使用です。 ポインターに基づくポインターで構成されるリンク リストをディスクに保存でき、メモリ内の別の場所に再読み込みしても、ポインターは有効なままです。 例:

```cpp
// based_pointers1.cpp
// compile with: /c
void *vpBuffer;
struct llist_t {
   void __based( vpBuffer ) *vpData;
   struct llist_t __based( vpBuffer ) *llNext;
};
```

ポインター `vpBuffer` には、プログラムの後の段階で割り当てられるメモリ アドレスが代入されます。 リンク リストは `vpBuffer` の値を基準として再配置されます。

> [!NOTE]
>  ポインターを含む識別子の永続化は、[メモリマップトファイル](/windows/win32/Memory/file-mapping)を使用して行うこともできます。

based ポインターを逆参照する場合、ベースは、明示的に指定されているか、または宣言によって暗黙的に認識されている必要があります。

以前のバージョンとの互換性のために、コンパイラオプション[/za \(無効になっている言語拡張)](../build/reference/za-ze-disable-language-extensions.md)が指定されていない場合、 **_based**は **__based**のシノニムになります。

## <a name="example"></a>使用例

次のコードは、ベースの変更による based ポインターの変更を示します。

```cpp
// based_pointers2.cpp
// compile with: /EHsc
#include <iostream>

int a1[] = { 1,2,3 };
int a2[] = { 10,11,12 };
int *pBased;

typedef int __based(pBased) * pBasedPtr;

using namespace std;
int main() {
   pBased = &a1[0];
   pBasedPtr pb = 0;

   cout << *pb << endl;
   cout << *(pb+1) << endl;

   pBased = &a2[0];

   cout << *pb << endl;
   cout << *(pb+1) << endl;
}
```

```Output
1
2
10
11
```

## <a name="see-also"></a>参照

[キーワード](../cpp/keywords-cpp.md)<br/>
[alloc_text](../preprocessor/alloc-text.md)