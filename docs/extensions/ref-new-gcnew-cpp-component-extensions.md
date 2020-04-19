---
title: ref new、gcnew (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
ms.openlocfilehash: f3dd0b73e300b44cb4f35e42683725813453d7de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516647"
---
# <a name="ref-new-gcnew--ccli-and-ccx"></a>ref new、gcnew (C++/CLI および C++/CX)

**ref new** 集計キーワードは、オブジェクトがアクセスできなくなったときにガベージ コレクションによって収集され、割り当てられたオブジェクトへのハンドル ([^](handle-to-object-operator-hat-cpp-component-extensions.md)) を返す型のインスタンスを割り当てます。

## <a name="all-runtimes"></a>すべてのランタイム

**ref new** によって割り当てられた型のインスタンスのメモリは、自動的に解放されます。

**ref new** 演算では、メモリを割り当てることができない場合は `OutOfMemoryException` がスローされます。

ネイティブ C++ 型のメモリの割り当てと解放の詳細については、「[new 演算子と delete 演算子](../cpp/new-and-delete-operators.md)」を参照してください。

## <a name="windows-runtime"></a>Windows ランタイム

有効期間が自動的に管理される Windows ランタイム オブジェクトのメモリを割り当てるには、**ref new** を使用します。 オブジェクトは、参照の最後のコピーがスコープ外になった後で参照カウントが 0 になると、自動的に解放されます。 詳細については、「[Ref クラスと構造体](../cppcx/ref-classes-and-structs-c-cx.md)」を参照してください。

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

マネージド型 (参照型または値型) のメモリは **gcnew** によって割り当てられ、ガベージ コレクションによって解放されます。

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次の例では、**gcnew** を使用して Message オブジェクトを割り当てています。

```cpp
// mcppv2_gcnew_1.cpp
// compile with: /clr
ref struct Message {
   System::String^ sender;
   System::String^ receiver;
   System::String^ data;
};

int main() {
   Message^ h_Message  = gcnew Message;
  //...
}
```

次の例では、**gcnew** を使用して、参照型のように使用するボックス化された値型を作成しています。

```cpp
// example2.cpp : main project file.
// compile with /clr
using namespace System;
value class Boxed {
    public:
        int i;
};
int main()
{
    Boxed^ y = gcnew Boxed;
    y->i = 32;
    Console::WriteLine(y->i);
    return 0;
}
```

```Output
32
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)