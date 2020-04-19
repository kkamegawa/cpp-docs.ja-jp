---
title: const ポインターと volatile ポインター
ms.date: 11/19/2019
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
ms.openlocfilehash: c0aafde9070275abcb270710e2d4a7a8d9806267
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246629"
---
# <a name="const-and-volatile-pointers"></a>const ポインターと volatile ポインター

[Const](const-cpp.md)および[volatile](volatile-cpp.md)キーワードは、ポインターの処理方法を変更します。 **Const**キーワードは、初期化後にポインターを変更できないことを指定します。ポインターは、それ以降は変更されないように保護されています。

**Volatile**キーワードは、後に続く名前に関連付けられている値を、ユーザーアプリケーション以外のアクションで変更できることを指定します。 そのため、 **volatile**キーワードは、割り込みサービスルーチンとの通信に使用される複数のプロセスまたはグローバルデータ領域からアクセスできる共有メモリ内のオブジェクトを宣言する場合に便利です。

名前が**volatile**として宣言されている場合、コンパイラはプログラムによってアクセスされるたびに、メモリから値を再読み込みします。 これによって、可能な最適化が大幅に減少します。 ただし、オブジェクトの状態が予期せず変わる場合、これが予測可能なプログラムの実行を保証する唯一の方法になります。

ポインターが指すオブジェクトを**const**または**volatile**として宣言するには、次の形式の宣言を使用します。

```cpp
const char *cpch;
volatile char *vpch;
```

ポインターの値 (つまり、ポインターに格納されている実際のアドレス) を**const**または**volatile**として宣言するには、次の形式の宣言を使用します。

```cpp
char * const pchc;
char * volatile pchv;
```

このC++言語では、 **const**として宣言されたオブジェクトまたはポインターの変更を許可する割り当てが禁止されています。 このような代入を実行すると、オブジェクトまたはポインターを宣言したときの情報が削除されるため、元の宣言の意図に反することになります。 次に宣言の例を示します。

```cpp
const char cch = 'A';
char ch = 'B';
```

上記の2つのオブジェクト (`cch`、 **const char**型の、`ch`型の宣言 **)** に対して、次の宣言/初期化が有効になります。

```cpp
const char *pch1 = &cch;
const char *const pch4 = &cch;
const char *pch5 = &ch;
char *pch6 = &ch;
char *const pch7 = &ch;
const char *const pch8 = &ch;
```

次の宣言と初期化はエラーになります。

```cpp
char *pch2 = &cch;   // Error
char *const pch3 = &cch;   // Error
```

`pch2` の宣言は、定数オブジェクトを変更する可能性があるポインターを宣言するため、許可されません。 `pch3` の宣言は、ポインターがオブジェクトではなく定数であることを指定します。宣言は、`pch2` 宣言が許可されていないのと同じ理由で許可されていません。

次の 8 つの代入は、ポインターを介した代入と、前に宣言したポインター値の変更を示しています。ここでは、初期化が `pch1` から `pch8` まで正しかったと仮定します。

```cpp
*pch1 = 'A';  // Error: object declared const
pch1 = &ch;   // OK: pointer not declared const
*pch2 = 'A';  // OK: normal pointer
pch2 = &ch;   // OK: normal pointer
*pch3 = 'A';  // OK: object not declared const
pch3 = &ch;   // Error: pointer declared const
*pch4 = 'A';  // Error: object declared const
pch4 = &ch;   // Error: pointer declared const
```

**Volatile**として宣言されたポインター、または**const**と**volatile**の組み合わせとして宣言されたポインターは、同じ規則に従います。

**Const**オブジェクトへのポインターは、次のように関数宣言でよく使用されます。

```cpp
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );
```

前のステートメントでは、 [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)関数を宣言しています。ここで、3つの引数のうちの2つは**char**へのポインター型です。 引数は値ではなく参照によって渡されるので、`strSource` が**const**として宣言されていない場合、関数は `strDestination` と `strSource` の両方を自由に変更できます。 `strSource` を**const**として宣言すると、呼び出し元は、呼び出された関数によって変更できない `strSource` を保証します。

> [!NOTE]
> *Typename* <strong>\*</strong>から**const** *typename* <strong>\*</strong>への標準変換があるため、型 `char *` の引数を[strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)に渡すことは有効です。 ただし、この逆は当てはまりません。オブジェクトまたはポインターから**const**属性を削除するための暗黙的な変換は存在しません。

指定された型の**const**ポインターは、同じ型のポインターに割り当てることができます。 ただし、 **const**でないポインターを**const**ポインターに割り当てることはできません。 次のコードは、正しい代入と正しくない代入を示します。

```cpp
// const_pointer.cpp
int *const cpObject = 0;
int *pObject;

int main() {
pObject = cpObject;
cpObject = pObject;   // C3892
}
```

次のサンプルは、オブジェクトへのポインターへのポインターがあるとき、オブジェクトを定数として宣言する方法を示します。

```cpp
// const_pointer2.cpp
struct X {
   X(int i) : m_i(i) { }
   int m_i;
};

int main() {
   // correct
   const X cx(10);
   const X * pcx = &cx;
   const X ** ppcx = &pcx;

   // also correct
   X const cx2(20);
   X const * pcx2 = &cx2;
   X const ** ppcx2 = &pcx2;
}
```

## <a name="see-also"></a>参照

[ポインター](pointers-cpp.md)
[生のポインター](raw-pointers.md)