---
title: '左辺値参照宣言子: &amp;'
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
ms.openlocfilehash: 7710b6f1efc2de770b26ad50923bde2ee5200f61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209555"
---
# <a name="lvalue-reference-declarator-amp"></a>左辺値参照宣言子: &amp;

オブジェクトのアドレスを保持しますが、オブジェクトのように構文的に実行されます。

## <a name="syntax"></a>構文

```
type-id & cast-expression
```

## <a name="remarks"></a>Remarks

lvalue 参照は、オブジェクトの別名と考えることができます。 左辺値参照の宣言は、参照宣言子が続く指定子のオプションのリストから構成されます。 参照は初期化する必要があり、変更できません。

アドレスを特定のポインター型に変換できるオブジェクトは、類似した参照型にも変換できます。 たとえば、アドレスを `char *` 型に変換できるオブジェクトは、`char &` 型にも変換できます。

参照の宣言の使用を混同しないでください、 [address-of 演算子](../cpp/address-of-operator-amp.md)します。 ときに、 `&`*識別子*など、型の前が**int**または**char**、*識別子*への参照として宣言されています型。 ときに`&`*識別子*前がない型で、使用状況は、address-of 演算子の。

## <a name="example"></a>例

次の例は、`Person` オブジェクトの宣言による参照宣言子と、そのオブジェクトへの参照を示します。 `rFriend` は `myFriend` への参照であるため、いずれかの変数を更新すると同じオブジェクトが変更されます。

```cpp
// reference_declarator.cpp
// compile with: /EHsc
// Demonstrates the reference declarator.
#include <iostream>
using namespace std;

struct Person
{
    char* Name;
    short Age;
};

int main()
{
   // Declare a Person object.
   Person myFriend;

   // Declare a reference to the Person object.
   Person& rFriend = myFriend;

   // Set the fields of the Person object.
   // Updating either variable changes the same object.
   myFriend.Name = "Bill";
   rFriend.Age = 40;

   // Print the fields of the Person object to the console.
   cout << rFriend.Name << " is " << myFriend.Age << endl;
}
```

```Output
Bill is 40
```

## <a name="see-also"></a>関連項目

[参照](../cpp/references-cpp.md)<br/>
[参照型関数の引数](../cpp/reference-type-function-arguments.md)<br/>
[参照型関数の戻り値](../cpp/reference-type-function-returns.md)<br/>
[ポインターへの参照](../cpp/references-to-pointers.md)