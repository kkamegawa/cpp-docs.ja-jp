---
title: '方法: アンマネージ メモリ内のオブジェクト参照を保持します。'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- object references, in native functions
- objects [C++], reference in native functions
- references, to objects in native functions
- gcroot keyword [C++], object reference in native function
ms.assetid: a61eb8ce-3982-477d-8d3d-2173fd57166d
ms.openlocfilehash: 0d8dc341d1fe2c61eba098abec9258a2c6dade79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387293"
---
# <a name="how-to-hold-object-reference-in-unmanaged-memory"></a>方法: アンマネージ メモリ内のオブジェクト参照を保持します。

ラップする gcroot.h を使用することができます<xref:System.Runtime.InteropServices.GCHandle>をアンマネージ メモリ内の CLR オブジェクトの参照を保持します。 また、使用することができます`GCHandle`直接します。

## <a name="example"></a>例

```
// hold_object_reference.cpp
// compile with: /clr
#include "gcroot.h"
using namespace System;

#pragma managed
class StringWrapper {

private:
   gcroot<String ^ > x;

public:
   StringWrapper() {
      String ^ str = gcnew String("ManagedString");
      x = str;
   }

   void PrintString() {
      String ^ targetStr = x;
      Console::WriteLine("StringWrapper::x == {0}", targetStr);
   }
};
#pragma unmanaged
int main() {
   StringWrapper s;
   s.PrintString();
}
```

```Output
StringWrapper::x == ManagedString
```

## <a name="example"></a>例

`GCHandle` アンマネージ メモリ内のマネージ オブジェクトの参照を保持するための手段が表示されます。  使用する、<xref:System.Runtime.InteropServices.GCHandle.Alloc%2A>マネージ オブジェクトへの非透過ハンドルを作成するメソッドをおよび<xref:System.Runtime.InteropServices.GCHandle.Free%2A>を解放します。 また、<xref:System.Runtime.InteropServices.GCHandle.Target%2A>メソッドでは、マネージ コードでハンドルからオブジェクト参照を取得できます。

```
// hold_object_reference_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed
class StringWrapper {
   IntPtr m_handle;
public:
   StringWrapper() {
      String ^ str = gcnew String("ManagedString");
      m_handle = static_cast<IntPtr>(GCHandle::Alloc(str));
   }
   ~StringWrapper() {
      static_cast<GCHandle>(m_handle).Free();
   }

   void PrintString() {
      String ^ targetStr = safe_cast< String ^ >(static_cast<GCHandle>(m_handle).Target);
      Console::WriteLine("StringWrapper::m_handle == {0}", targetStr);
   }
};

#pragma unmanaged
int main() {
   StringWrapper s;
   s.PrintString();
}
```

```Output
StringWrapper::m_handle == ManagedString
```

## <a name="see-also"></a>関連項目

[C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)
