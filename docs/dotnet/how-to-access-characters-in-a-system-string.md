---
title: '方法: System::string の文字をアクセス'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
ms.openlocfilehash: 6b9e30a18ab1d2b8463ccccae0b265bc20904020
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222937"
---
# <a name="how-to-access-characters-in-a-systemstring"></a>方法: System::string の文字をアクセス

文字にアクセスすることができます、<xref:System.String>オブジェクトの高パフォーマンスの呼び出しをアンマネージ関数を受け取る`wchar_t*`文字列。 メソッド生成の最初の文字への内部ポインター、<xref:System.String>オブジェクト。 このポインターの直接操作またはピン留めし、通常、関数に渡すことができますが`wchar_t`文字列。

## <a name="example"></a>例

`PtrToStringChars` 返します、 <xref:System.Char>、内部ポインターである (とも呼ばれる、 `byref`)。 そのため、ガベージ コレクションの対象になります。 ネイティブ関数に渡すしようとしている場合を除き、このポインターをピン留めする必要はありません。

次のコードについて考えてみましょう。  ピン留めは必要ありませんので`ppchar`、内部ポインターであり、ガベージ コレクターは、文字列の指すを移動する場合は更新も`ppchar`します。 なし、 [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md)、コードを実行およびが潜在的なパフォーマンスの影響によるものをピン留めします。

渡した場合`ppchar`、ネイティブ関数にする必要があります固定ポインター。 ガベージ コレクターがアンマネージ スタック フレーム上のポインターを更新することができません。

```
// PtrToStringChars.cpp
// compile with: /clr
#include<vcclr.h>
using namespace System;

int main() {
   String ^ mystring = "abcdefg";

   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );

   for ( ; *ppchar != L'\0'; ++ppchar )
      Console::Write(*ppchar);
}
```

```Output
abcdefg
```

## <a name="example"></a>例

この例は、ピン留めが必要な場所を示します。

```
// PtrToStringChars_2.cpp
// compile with: /clr
#include <string.h>
#include <vcclr.h>
// using namespace System;

size_t getlen(System::String ^ s) {
   // Since this is an outside string, we want to be secure.
   // To be secure, we need a maximum size.
   size_t maxsize = 256;
   // make sure it doesn't move during the unmanaged call
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);
   return wcsnlen(pinchars, maxsize);
};

int main() {
   System::Console::WriteLine(getlen("testing"));
}
```

```Output
7
```

## <a name="example"></a>例

内部ポインターには、ネイティブ C++ ポインターのすべてのプロパティがあります。 たとえば、リンクされているデータ構造を確認し、挿入と削除が 1 つだけのポインターを使用して使用できます。

```
// PtrToStringChars_3.cpp
// compile with: /clr /LD
using namespace System;
ref struct ListNode {
   Int32 elem;
   ListNode ^ Next;
};

void deleteNode( ListNode ^ list, Int32 e ) {
   interior_ptr<ListNode ^> ptrToNext = &list;
   while (*ptrToNext != nullptr) {
      if ( (*ptrToNext) -> elem == e )
         *ptrToNext = (*ptrToNext) -> Next;   // delete node
      else
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node
   }
}
```

## <a name="see-also"></a>関連項目

[C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)
