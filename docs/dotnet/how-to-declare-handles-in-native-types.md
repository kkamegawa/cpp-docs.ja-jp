---
title: '方法: ネイティブ型のハンドルを宣言します。'
ms.custom: get-started-article
ms.date: 11/04/2016
f1_keywords:
- gcroot
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
ms.openlocfilehash: f5d6d31be9f3c10e1a56639ccf20663ce59d7941
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387410"
---
# <a name="how-to-declare-handles-in-native-types"></a>方法: ネイティブ型のハンドルを宣言します。

ネイティブ型のハンドル型を宣言することはできません。 vcclr.h でタイプ セーフ ラッパー テンプレートを提供する`gcroot`C++ ヒープから CLR オブジェクトを参照します。 このテンプレートでは、ネイティブ型に仮想のハンドルを埋め込むし、基になる型の場合と同様に扱うことできます。 ほとんどの場合、使用することができます、`gcroot`キャストは必要ありません、埋め込み型としてのオブジェクト。 ただし、[ごとで](../dotnet/for-each-in.md)を使用して`static_cast`を基になるマネージ参照を取得します。

`gcroot`テンプレートは、ガベージ コレクション ヒープに「ハンドル」を提供する、System::Runtime::InteropServices::GCHandle 値クラスの機能を使用して実装されます。 処理自体がガベージ コレクションでないことに注意してくださいし、のデストラクターによって使用されていないときに解放される、`gcroot`クラス (このデストラクターは手動で呼び出すことはできません)。 インスタンス化する場合、`gcroot`呼び出す必要がありますが、ネイティブ ヒープのオブジェクト リソースを削除します。

ランタイムは、ハンドルと、参照する CLR オブジェクト間の関連付けを維持します。 CLR オブジェクトは、ガベージ コレクション ヒープに移動したとき、ハンドルは、オブジェクトの新しいアドレスを返します。 変数に割り当てられる前にピン留めする必要はありません、`gcroot`テンプレート。

## <a name="example"></a>例

このサンプルを作成する方法を示しています、`gcroot`ネイティブ スタック上のオブジェクト。

```
// mcpp_gcroot.cpp
// compile with: /clr
#include <vcclr.h>
using namespace System;

class CppClass {
public:
   gcroot<String^> str;   // can use str as if it were String^
   CppClass() {}
};

int main() {
   CppClass c;
   c.str = gcnew String("hello");
   Console::WriteLine( c.str );   // no cast required
}
```

```Output
hello
```

## <a name="example"></a>例

このサンプルを作成する方法を示しています、`gcroot`ネイティブ ヒープのオブジェクト。

```
// mcpp_gcroot_2.cpp
// compile with: /clr
// compile with: /clr
#include <vcclr.h>
using namespace System;

struct CppClass {
   gcroot<String ^> * str;
   CppClass() : str(new gcroot<String ^>) {}

   ~CppClass() { delete str; }

};

int main() {
   CppClass c;
   *c.str = gcnew String("hello");
   Console::WriteLine( *c.str );
}
```

```Output
hello
```

## <a name="example"></a>例

このサンプルは、使用する方法を示します`gcroot`をネイティブ型を使用して値型 (参照型ではなく) への参照を保持するために`gcroot`ボックス化された型にします。

```
// mcpp_gcroot_3.cpp
// compile with: /clr
#include < vcclr.h >
using namespace System;

public value struct V {
   String^ str;
};

class Native {
public:
   gcroot< V^ > v_handle;
};

int main() {
   Native native;
   V v;
   native.v_handle = v;
   native.v_handle->str = "Hello";
   Console::WriteLine("String in V: {0}", native.v_handle->str);
}
```

```Output
String in V: Hello
```

## <a name="see-also"></a>関連項目

[C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)
