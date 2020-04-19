---
title: コンパイラの警告 (レベル 1) C4342
ms.date: 11/04/2016
f1_keywords:
- C4342
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
ms.openlocfilehash: 439c4976f25688fd9220c3f58ceb933266b5f15c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187510"
---
# <a name="compiler-warning-level-1-c4342"></a>コンパイラの警告 (レベル 1) C4342

動作変更: '*関数*' 呼び出されると、メンバー演算子が以前のバージョンで呼び出されましたが、

Visual Studio 2002 の前に Visual C のバージョンでは、メンバーが呼び出されると、この動作が変更されていて、コンパイラは、名前空間スコープで最適な一致を検索するようになりました。

メンバー演算子が見つかった場合、コンパイラは以前は考えない任意の名前空間スコープ演算子。 名前空間スコープでより優れた一致がある場合、現在のコンパイラ正しく呼び出し、一方、以前のコンパイラが考慮されません。

現在のバージョンにコードを正しくに移植した後、この警告を無効にする必要があります。  コンパイラは偽陽性、コードには、この警告を生成する動作の変更がないです。

既定では、この警告はオフに設定されています。 詳細については、「 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)」を参照してください。

次の例では、C4342 が生成されます。

```cpp
// C4342.cpp
// compile with: /EHsc /W1
#include <fstream>
#pragma warning(default: 4342)
using namespace std;
struct X : public ofstream {
   X();
};

X::X() {
   open( "ofs_bug_ev.txt." );
   if ( is_open() ) {
      *this << "Text" << "<-should be text" << endl;   // C4342
      *this << ' ' << "<-should be space symbol" << endl;   // C4342
   }
}

int main() {
   X b;
   b << "Text" << "<-should be text" << endl;
   b << ' ' << "<-should be space symbol" << endl;
}
```