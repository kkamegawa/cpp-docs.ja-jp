---
title: コンパイラ エラー C3899
ms.date: 11/04/2016
f1_keywords:
- C3899
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
ms.openlocfilehash: 022bc1a37f7d9cfdb2c206592dd303a9c3c95080
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749114"
---
# <a name="compiler-error-c3899"></a>コンパイラ エラー C3899

' var ': initonly データメンバーの左辺値は、クラス ' class ' の並行領域内で直接使用することはできません

[Initonly (C++/cli)](../../dotnet/initonly-cpp-cli.md)データメンバーは、[並列](../../parallel/openmp/reference/parallel.md)領域内のコンストラクターのその部分で初期化することはできません。  これは、コンパイラがそのコードの内部再配置を行うためです。そのため、実質的にはコンストラクターの一部ではなくなります。

解決するには、コンストラクターで initonly データメンバーを初期化しますが、並列領域の外側で初期化します。

## <a name="example"></a>使用例

次の例では、C3899 が生成されます。

```cpp
// C3899.cpp
// compile with: /clr /openmp
#include <omp.h>

public ref struct R {
   initonly int x;
   R() {
      x = omp_get_thread_num() + 1000;   // OK
      #pragma omp parallel num_threads(5)
      {
         // cannot assign to 'x' here
         x = omp_get_thread_num() + 1000;   // C3899
         System::Console::WriteLine("thread {0}", omp_get_thread_num());
      }
      x = omp_get_thread_num() + 1000;   // OK
   }
};

int main() {
   R^ r = gcnew R;
   System::Console::WriteLine(r->x);
}
```
