---
title: '方法: 構造体のマーシャ リングを使用して C++ 相互運用'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Interop, structures
- structures [C++], marshaling
- data marshaling [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
ms.openlocfilehash: 93aeabc3fe984bee8a9281281320d61dccd182bf
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345699"
---
# <a name="how-to-marshal-structures-using-c-interop"></a>方法: 構造体のマーシャ リングを使用して C++ 相互運用

このトピックでは、Visual C の相互運用性の 1 つのファセットを示します。 詳細については、次を参照してください。[を使用して C++ Interop (暗黙の PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)します。

次のコード例、[マネージ、アンマネージ](../preprocessor/managed-unmanaged.md)#pragma ディレクティブを実装するマネージ コードと同じファイル内の関数をアンマネージが個別のファイルに定義されている場合、これらの関数が同じ方法で相互運用。 アンマネージ関数のみを含むファイルを使用してコンパイルする必要はありません[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)します。

## <a name="example"></a>例

次の例では、マネージからアンマネージ関数では、両方の値と参照渡しで構造体を渡す方法を示します。 この例では構造体にのみ簡単な組み込みのデータ型が含まれているため (を参照してください[blittable 型と非 Blittable 型](/dotnet/framework/interop/blittable-and-non-blittable-types))、特殊なマーシャ リングする必要はありません。 ポインターが含まれるものなど、blittable でない構造体をマーシャ リングする、次を参照してください。[方法。埋め込み C++ Interop を使用して、ポインターをマーシャ リング](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)します。

```
// PassStruct1.cpp
// compile with: /clr

#include <stdio.h>
#include <math.h>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

struct Location {
   int x;
   int y;
};

double GetDistance(Location loc1, Location loc2) {
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   printf_s("[unmanaged] Initializing location...\n");
   lp->x = 50;
   lp->y = 50;
}

#pragma managed

int main() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   Location loc3;
   InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

## <a name="example"></a>例

次の例では、アンマネージからマネージ関数では、両方の値と参照渡しで構造体を渡す方法を示します。 この例では構造体にのみ簡単な組み込みのデータ型が含まれているため (を参照してください[blittable 型と非 Blittable 型](/dotnet/framework/interop/blittable-and-non-blittable-types))、特殊なマーシャ リングする必要はありません。 ポインターが含まれるものなど、blittable でない構造体をマーシャ リングする、次を参照してください。[方法。埋め込み C++ Interop を使用して、ポインターをマーシャ リング](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)します。

```
// PassStruct2.cpp
// compile with: /clr
#include <stdio.h>
#include <math.h>
using namespace System;

// native structure definition
struct Location {
   int x;
   int y;
};

#pragma managed

double GetDistance(Location loc1, Location loc2) {
   Console::Write("[managed] got loc1({0},{1})", loc1.x, loc1.y);
   Console::WriteLine(" loc2({0},{1})", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   Console::WriteLine("[managed] Initializing location...");
   lp->x = 50;
   lp->y = 50;
}

#pragma unmanaged

int UnmanagedFunc() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   printf_s("(unmanaged) loc1=(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2=(%d,%d)\n", loc2.x, loc2.y);

   double dist = GetDistance(loc1, loc2);
   printf_s("[unmanaged] distance = %f\n", dist);

   Location loc3;
   InitLocation(&loc3);
   printf_s("[unmanaged] got x=%d y=%d\n", loc3.x, loc3.y);

    return 0;
}

#pragma managed

int main() {
   UnmanagedFunc();
}
```

## <a name="see-also"></a>関連項目

[C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)
