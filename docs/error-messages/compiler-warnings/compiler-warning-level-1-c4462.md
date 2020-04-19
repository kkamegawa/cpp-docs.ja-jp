---
title: コンパイラの警告 (レベル 1) C4462
ms.date: 10/25/2017
f1_keywords:
- C4462
helpviewer_keywords:
- C4462
ms.assetid: 4e20aca4-293e-4c75-a83d-961c27ab7840
ms.openlocfilehash: bd4d5c1fd7dd8d7419fc901149ceab7e769e7076
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404053"
---
# <a name="compiler-warning-level-1-c4462"></a>コンパイラの警告 (レベル 1) C4462

> 型の GUID を特定できません。 プログラムは、実行時に失敗する可能性があります。

C4462 警告は、パブリックな `TypedEventHandler` に、型パラメーターの 1 つとして外側のクラスへの参照が含まれる場合に、Windows ランタイム アプリケーションまたはコンポーネントで発生します。

この警告は、自動的にエラーになります。 この動作を変更する場合を使用して、 [#pragma warning](../../preprocessor/warning.md)します。 たとえば、C4462 に、レベル 4 の警告を発行するために、この行をソース コード ファイルに追加します。

```cpp
#pragma warning(4:4462)
```

## <a name="example"></a>例

この例では、C4462 警告が生成されます。

```cpp
namespace N
{
    public ref struct EventArgs sealed {};
    public ref struct R sealed
    {
        R() {}
        event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
    };
}

[Platform::MTAThread]
int main()
{
    auto x = ref new N::R();
}
```

このエラーを回避する方法は 2 つあります。 1 つは、次の例に示すように、イベント内部のアクセシビリティを、同じ実行可能ファイル内のコードで使用できるように提供する方法です。このアクセシビリティは、他の Windows ランタイム コンポーネントのコードでは使用できないようにします。

```cpp
internal:
    event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
```

イベントがパブリックであることが求められる場合は、もう 1 つの方法で回避できます。この方法は既定のインターフェイスによって公開されます。

```cpp
ref struct R;
public interface struct IR{ event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;};

public ref struct R sealed : [Windows::Foundation::Metadata::Default] IR
{
    R() {}
    virtual event Windows::Foundation::TypedEventHandler<R ^, EventArgs^>^ e;
};
```

`Windows::Foundation::TypedEventHandler<R^, EventArgs^>^` 型の GUID が使用されるのは、他のコンポーネントからその型にアクセスする場合だけです。 最初の方法は、問題回避の後、独自のコンポーネント内でのみアクセスできるため機能します。 それ以外の場合、コンパイラは最悪の場合を想定する必要があり、警告を出力します。
