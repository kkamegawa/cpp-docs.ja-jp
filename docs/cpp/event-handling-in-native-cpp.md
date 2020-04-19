---
title: ネイティブ C++ でのイベント処理
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
ms.openlocfilehash: 9eb0334e3633921842fcc06155ba0300ff6192e1
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222182"
---
# <a name="event-handling-in-native-c"></a>ネイティブ C++ でのイベント処理

ネイティブC++を使用してイベント ソースとイベント レシーバーを設定すると、イベント処理、 [event_source](../windows/attributes/event-source.md)と[event_receiver](../windows/attributes/event-receiver.md)指定それぞれ属性`type` =`native`. これらの属性により、適用先のクラスは、イベントを発生させ、ネイティブの非 COM コンテキストでイベントを処理できます。

## <a name="declaring-events"></a>イベントの宣言

イベント ソース クラスで、使用、 [_ _event](../cpp/event.md)メソッドをイベントとして宣言するメソッド宣言でキーワード。 メソッドを宣言する必要がありますが、定義はしないでください。コンパイラは、イベント内でメソッドを暗黙的に定義するため、これを定義した場合、コンパイラ エラーが発生します。 ネイティブ イベントは、ゼロ以上のパラメーターを持つメソッドにできます。 戻り値の型は void または任意の整数型です。

## <a name="defining-event-handlers"></a>イベント ハンドラーの定義

イベント レシーバー クラスでは、イベント ハンドラーを定義します。イベント ハンドラーは、処理するイベントと一致するシグニチャ (戻り値の型、呼び出し規則、引数) を持つメソッドです。

## <a name="hooking-event-handlers-to-events"></a>イベントへのイベント ハンドラーのフック

組み込み関数を使用する、イベント レシーバー クラスでも[_ _hook](../cpp/hook.md)にイベントをイベント ハンドラーに関連付けると[_ _unhook](../cpp/unhook.md)イベント ハンドラーからイベントの関連付けを解除します。 複数のイベントを 1 つのイベント ハンドラーにフックすることも、複数のイベント ハンドラーを 1 つのイベントにフックすることもできます。

## <a name="firing-events"></a>イベントの発生

イベントを発生させるには、イベント ソース クラスのイベントとして宣言されたメソッドを呼び出します。 ハンドラーがイベントにフックされている場合は、ハンドラーが呼び出されます。

### <a name="native-c-event-code"></a>ネイティブ C++ イベント コード

次の例は、ネイティブ C++ でイベントを発生させる方法を示しています。 例をコンパイルして実行するには、コード内のコメントを参照してください。

## <a name="example"></a>例

### <a name="code"></a>コード

```cpp
// evh_native.cpp
#include <stdio.h>

[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};

[event_receiver(native)]
class CReceiver {
public:
   void MyHandler1(int nValue) {
      printf_s("MyHandler1 was called with value %d.\n", nValue);
   }

   void MyHandler2(int nValue) {
      printf_s("MyHandler2 was called with value %d.\n", nValue);
   }

   void hookEvent(CSource* pSource) {
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }

   void unhookEvent(CSource* pSource) {
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }
};

int main() {
   CSource source;
   CReceiver receiver;

   receiver.hookEvent(&source);
   __raise source.MyEvent(123);
   receiver.unhookEvent(&source);
}
```

### <a name="output"></a>Output

```Output
MyHandler2 was called with value 123.
MyHandler1 was called with value 123.
```

## <a name="see-also"></a>関連項目

[イベント処理](../cpp/event-handling.md)