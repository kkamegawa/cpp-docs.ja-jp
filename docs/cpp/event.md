---
title: __event
ms.date: 11/04/2016
f1_keywords:
- __event_cpp
- __event
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
ms.openlocfilehash: 3a837e30d3cd66f7caa9b44971f432e00b0917ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154426"
---
# <a name="__event"></a>__event

イベントを宣言します。

## <a name="syntax"></a>構文

```
__event method-declarator;
__event __interface interface-specifier;
__event member-declarator;
```

## <a name="remarks"></a>Remarks

キーワード **_ _event**メソッドの宣言、インターフェイス宣言、またはデータ メンバーの宣言に適用できます。 ただし、使用することはできません、 **_ _event**キーワードを入れ子になったクラスのメンバーを修飾します。

イベント ソースとイベント レシーバーがネイティブ C++、COM、またはマネージド (.NET Framework) であるかによって、次の構成体をイベントとして使用できます。

|ネイティブ C++|COM|マネージド (.NET Framework)|
|------------------|---------|--------------------------------|
|メソッド|—|メソッド|
|—|interface|—|
|—|—|データ メンバー|

使用[_ _hook](../cpp/hook.md)ハンドラー メソッドをイベント メソッドに関連付けるには、イベント レシーバーでします。 後のイベントを作成することに注意して、 **_ _event**キーワード、イベントが呼び出されると、その後、そのイベントにフックすべてのイベント ハンドラーが呼び出されます。

**_ _Event**メソッドの宣言は定義を持つことはできません。 定義を暗黙的に生成されると、通常のメソッドの場合と同様、イベントのメソッドを呼び出せるようにします。

> [!NOTE]
>  テンプレート クラスまたは構造体にイベントを含めることはできません。

## <a name="native-events"></a>ネイティブ イベント

ネイティブ イベントはメソッドです。 戻り値の型は、通常、HRESULT または**void**、任意の整数型を指定できますなど、 **enum**します。 イベントが整数の戻り値の型を使用していて、イベント ハンドラーがゼロ以外の値を返すときのエラー条件が定義されていると、発生するイベントは他のデリゲートを呼び出します。

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

参照してください[ネイティブ C++ でのイベント処理](../cpp/event-handling-in-native-cpp.md)サンプル コードについてはします。

## <a name="com-events"></a>COM イベント

COM イベントはインターフェイスです。 イベント ソース インターフェイスのメソッドのパラメーターがある*で*パラメーター (ただし、これは厳格に強制されていません)、ため、*アウト*パラメーターはマルチキャストした場合に便利です。 使用する場合に、レベル 1 の警告が発行される、*アウト*パラメーター。

戻り値の型は、通常、HRESULT または**void**、任意の整数型を指定できますが、含む**enum**します。 イベントが整数の戻り値の型を使用していて、イベント ハンドラーがゼロ以外の値を返すと、これはエラー状態であり、発生するイベントは他のデリゲートの呼び出しをアボートします。 コンパイラはイベント ソース インターフェイスとしてのマークで自動的に注意してください、[ソース](../windows/attributes/source-cpp.md)生成された IDL にします。

[_ _Interface](../cpp/interface.md)キーワードの後に必要なは常に **_ _event** COM イベント ソース。

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

参照してください[COM でのイベント処理](../cpp/event-handling-in-com.md)サンプル コードについてはします。

## <a name="managed-events"></a>マネージド イベント

新しい構文でイベントのコーディングについては、次を参照してください。[イベント](../extensions/event-cpp-component-extensions.md)します。

マネージド イベントは、データ メンバーまたはメソッドです。 イベントと共に使用すると、デリゲートの戻り値の型が準拠する必要があります、[共通言語仕様](/dotnet/standard/language-independence-and-language-independent-components)します。 イベント ハンドラーの戻り値の型は、デリゲートの戻り値の型と一致する必要があります。 デリゲートの詳細については、次を参照してください。[デリゲートとイベント](../dotnet/delegates-and-events.md)します。 マネージド イベントがメンバー関数である場合、その型はデリゲートへのポインターでなければなりません。

.NET Framework では、それ自身がメソッド (つまり、対応するデリゲートの `Invoke` メソッド) であるかのようにデータ メンバーを処理できます。 マネージド イベント データ メンバーを宣言するためのデリゲート型を事前に定義する必要があります。 これに対し、マネージド イベント メソッドは、まだ定義されていない場合、対応するマネージド デリゲートを暗黙的に定義します。 たとえば、次のように、`OnClick` などのイベント値をイベントとして宣言できます。

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

マネージド イベントを暗黙的に宣言するときは、イベント ハンドラーが追加または削除されたときに呼び出される追加および削除アクセサーを指定できます。 クラスの外部からイベントを呼び出す (発生させる) メソッドを定義することもできます。

## <a name="example-native-events"></a>例:ネイティブ イベント

```cpp
// EventHandling_Native_Event.cpp
// compile with: /c
[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};
```

## <a name="example-com-events"></a>例:COM イベント

```cpp
// EventHandling_COM_Event.cpp
// compile with: /c
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];

[ dual, uuid("00000000-0000-0000-0000-000000000002") ]
__interface IEventSource {
   [id(1)] HRESULT MyEvent();
};
[ coclass, uuid("00000000-0000-0000-0000-000000000003"),  event_source(com) ]
class CSource : public IEventSource {
public:
   __event __interface IEventSource;
   HRESULT FireEvent() {
      __raise MyEvent();
      return S_OK;
   }
};
```

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)<br/>
[イベント処理](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)