---
title: コンパイラ エラー C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: f23c2a38f8e4d6781af73fb70a25cf4737e2c4e8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758776"
---
# <a name="compiler-error-c2261"></a>コンパイラ エラー C2261

' string ': アセンブリ参照は無効であるため、解決できません

値が無効です。

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> は、フレンドアセンブリを指定するために使用されます。 たとえば、.dll で b .dll をフレンドアセンブリとして指定する場合は、(.dll 内) を指定します。 InternalsVisibleTo ("b") です。 次に、ランタイムは .dll 内のすべての情報にアクセスできるようにします (プライベート型を除く)。

フレンドアセンブリを指定するときの正しい構文の詳細については、「 [Friend assemblies (C++)](../../dotnet/friend-assemblies-cpp.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C2261 が生成されます。

```cpp
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```
