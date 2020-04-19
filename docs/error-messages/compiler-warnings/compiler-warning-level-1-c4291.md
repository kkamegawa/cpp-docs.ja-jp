---
title: コンパイラの警告 (レベル 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: c8dc35a58d40d2619f6e035e07b4ad0b3351c45d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626638"
---
# <a name="compiler-warning-level-1-c4291"></a>コンパイラの警告 (レベル 1) C4291

' 宣言 ': 一致する演算子の削除が見つかりませんでした。初期化が例外をスローした場合、メモリは解放されません

配置の[削除](../../cpp/delete-operator-cpp.md)がない場合は、配置の[新しい](../../cpp/new-operator-cpp.md)が使用されます。

Operator **new**を使用してオブジェクトにメモリが割り当てられると、オブジェクトのコンストラクターが呼び出されます。 コンストラクターが例外をスローした場合、そのオブジェクトに割り当てられたメモリの割り当てを解除する必要があります。 Operator **new**と一致する operator **delete**関数が存在しない限り、この操作を行うことはできません。

追加の引数を指定せずに**new**演算子を使用し、 [/gx](../../build/reference/gx-enable-exception-handling.md)、 [/ehs](../../build/reference/eh-exception-handling-model.md)、または/eha オプションでコンパイルして例外処理を有効にすると、コンパイラは、コンストラクターが例外をスローした場合に operator **delete**を呼び出すためのコードを生成します。

**New**演算子の placement 形式 (割り当てのサイズに加えて引数を持つフォーム) を使用し、オブジェクトのコンストラクターが例外をスローした場合でも、コンパイラは operator **delete**を呼び出すコードを生成します。ただし、これが行われるのは、メモリを割り当てた**new**演算子の配置形式と演算子の**削除**の配置形式が一致する場合だけです。 (例:

```cpp
// C4291.cpp
// compile with: /EHsc /W1
#include <malloc.h>

class CList
{
public:
   CList(int)
   {
      throw "Fail!";
   }
};

void* operator new(size_t size, char* pszFilename, int nLine)
{
   return malloc(size);
}

int main(void)
{
   try
   {
      // This will call ::operator new(unsigned int) to allocate heap
      // memory. Heap memory pointed to by pList1 will automatically be
      // deallocated by a call to ::operator delete(void*) when
      // CList::CList(int) throws an exception.
      CList* pList1 = new CList(10);
   }
   catch (...)
   {
   }

   try
   {
      // This will call the overloaded ::operator new(size_t, char*, int)
      // to allocate heap memory. When CList::CList(int) throws an
      // exception, ::operator delete(void*, char*, int) should be called
      // to deallocate the memory pointed to by pList2. Since
      // ::operator delete(void*, char*, int) has not been implemented,
      // memory will be leaked when the deallocation cannot occur.
      CList* pList2 = new(__FILE__, __LINE__) CList(20);   // C4291
   }
   catch (...)
   {
   }
}
```

上の例では、operator **new**の配置形式に一致する operator **delete**の配置形式が定義されていないため、警告 C4291 が生成されます。 この問題を解決するには、 **main**の上に次のコードを挿入します。 オーバーロードされた operator **delete**関数のパラメーターはすべて、最初のパラメーターを除く、オーバーロードされた演算子**new**のパラメーターと一致します。

```
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```