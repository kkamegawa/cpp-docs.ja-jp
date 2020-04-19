---
title: 静的メンバー (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- class members [C++], static
- instance constructors, static members
- class members [C++], shared
- members [C++], static data members
- static members [C++], data members
- static data members [C++]
- data members [C++], static data members
- class instances [C++], shared members
- instance constructors, shared members
- class instances [C++], static members
ms.assetid: 9cc8cf0f-d74c-46f2-8e83-42d4e42c8370
ms.openlocfilehash: 708f78c09db263584d478d16863999d4428e4891
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266947"
---
# <a name="static-members-c"></a>静的メンバー (C++)

クラスには、静的なメンバー データとメンバー関数を含めることができます。 データ メンバーとして宣言されている場合**static**データのコピーを 1 つだけでは、クラスのすべてのオブジェクトが保持されます。

静的データ メンバーは、特定のクラス型のオブジェクトの一部ではありません。 その結果、静的データ メンバーの宣言は定義とは見なされません。 データ メンバーはクラス スコープで宣言されますが、定義はファイル スコープで行われます。 これらの静的メンバーは外部リンケージを持ちます。 次に例を示します。

```cpp
// static_data_members.cpp
class BufferedOutput
{
public:
   // Return number of bytes written by any object of this class.
   short BytesWritten()
   {
      return bytecount;
   }

   // Reset the counter.
   static void ResetCount()
   {
      bytecount = 0;
   }

   // Static member declaration.
   static long bytecount;
};

// Define bytecount in file scope.
long BufferedOutput::bytecount;

int main()
{
}
```

上記のコードで、メンバー `bytecount` は、クラス `BufferedOutput` で宣言されていますが、クラス宣言の外側で定義する必要があります。

静的データ メンバーは、クラス型のオブジェクトを参照せずに参照できます。 `BufferedOutput` オブジェクトを使用して書き込まれたバイト数は、次のように取得できます。

```cpp
long nBytes = BufferedOutput::bytecount;
```

静的メンバーを存在させるために、クラス型のオブジェクトが存在する必要はありません。 静的メンバーは、メンバー選択を使用してアクセスすることもできます (**します。** **->** ) 演算子。 例:

```cpp
BufferedOutput Console;

long nBytes = Console.bytecount;
```

前のケースでは、オブジェクト (`Console`) への参照は評価されません。返される値は、静的オブジェクト `bytecount` の値です。

静的データ メンバーはクラス メンバーのアクセス規則に従うため、静的データ メンバーへのプライベート アクセスはクラス メンバー関数およびフレンドだけに許可されます。 これらの規則が記載されて[メンバー アクセス コントロール](../cpp/member-access-control-cpp.md)します。 例外は、静的データ メンバーが、そのアクセス制限にかかわらず、ファイルのスコープ内で定義されなければならないということです。 データ メンバーを明示的に初期化する場合は、初期化子を定義で指定する必要があります。

静的メンバーの型は、クラス名で修飾されていません。 型ではそのため、`BufferedOutput::bytecount`は**long**します。

## <a name="see-also"></a>関連項目

[クラスと構造体](../cpp/classes-and-structs-cpp.md)