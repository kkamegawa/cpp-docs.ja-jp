---
title: コンパイラの警告 (レベル 1) C4350
ms.date: 11/04/2016
f1_keywords:
- C4350
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
ms.openlocfilehash: 8f23751151d8d83c68608d926ef422d56dde41a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384206"
---
# <a name="compiler-warning-level-1-c4350"></a>コンパイラの警告 (レベル 1) C4350

動作変更: 'member1' が 'member2' の代わりに呼び出されました。

右辺値は、非定数の参照にバインドすることはできません。 Visual Studio 2003 の前に Visual C のバージョンでは、直接の初期化で非定数の参照を右辺値をバインドすることでした。 このコードでは、警告できるようになりました。

旧バージョンとの互換性のため、非定数の参照を右辺値をバインドすることも可能ですが、可能な場合は、標準変換が推奨されます。

この警告は、Visual C .NET 2002 のコンパイラからの動作の変更を表します。 有効な場合、この警告を正しいコードの指定された可能性がある可能性があります。 たとえば、でした指定する必要を使用する場合、 **std::auto_ptr**クラス テンプレートです。

この警告が発生した場合は、非定数の参照を右辺値をバインディングに依存する場合に表示するコードを調べます。 参照に定数を追加するか、追加の const 参照渡しオーバー ロードを提供するには、問題を解決できます。

既定では、この警告はオフに設定されています。 詳細については、「 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)」を参照してください。

次の例では、C4350 が生成されます。

```cpp
// C4350.cpp
// compile with: /W1
#pragma warning (default : 4350)
class A {};

class B
{
public:
   B(B&){}
   // try the following instead:
   // B(const B&){}

   B(A){}
   operator A(){ return A();}
};

B source() { return A(); }

int main()
{
   B ap(source());   // C4350
}
```