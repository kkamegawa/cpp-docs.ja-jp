---
title: コンパイラ エラー C3706
ms.date: 11/04/2016
f1_keywords:
- C3706
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
ms.openlocfilehash: 810ec59a814b04349913648fb49a03eb63912cd9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757983"
---
# <a name="compiler-error-c3706"></a>コンパイラ エラー C3706

' function ': COM イベントを発生させる COM インターフェイスでなければなりません。

COM イベントを発生させるために使用するイベントインターフェイスは、COM インターフェイスである必要があります。 この場合、インターフェイスは、視覚C++属性を使用して定義するか、または #import の embedded_idl 属性を持つタイプライブラリの[#import](../../preprocessor/hash-import-directive-cpp.md)を使用してインポートする必要があります。

COM イベントを使用するには、次のサンプルに示されている ATL ヘッダーファイルの `#include` 行が必要です。 このエラーを解決するには、インターフェイス定義に次の属性のいずれかを適用して (イベントインターフェイス)、COM インターフェイスを `IEvents` します。[オブジェクト](../../windows/object-cpp.md)、[デュアル](../../windows/dual.md)、または[ディスパッチ](../../windows/dispinterface.md)インターフェイス。

インターフェイスが MIDL によって生成されたヘッダーファイルからのものである場合、コンパイラは COM インターフェイスとして認識しません。

次の例では、C3706 が生成されます。

```cpp
// C3706.cpp
// compile with: /c
// C3706 expected
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(dll, name="idid", uuid="12341234-1234-1234-1234-123412341234")];

// Uncomment the following line to resolve.
// [object, uuid="12341234-1234-1234-1234-123412341237"]
__interface IEvents : IUnknown {
   HRESULT event1(/*[in]*/ int i);   // uncomment [in]
};

[dual, uuid="12341234-1234-1234-1234-123412341235"]
__interface IBase {
   HRESULT fireEvents();
};

[coclass, event_source(com), uuid="12341234-1234-1234-1234-123412341236"]
class CEventSrc : public IBase {
   public:
   __event __interface IEvents;

   HRESULT fireEvents() {
      HRESULT hr = IEvents_event1(123);
      return hr;
   }
};
```
