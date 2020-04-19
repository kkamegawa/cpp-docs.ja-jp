---
title: __identifier (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
ms.openlocfilehash: 80aade53bf1d1c9aa30c4b8c8fe59c2247fe3cfb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515787"
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)

C++ キーワードを識別子として使用できるようにします。

## <a name="all-platforms"></a>すべてのプラットフォーム

### <a name="syntax"></a>構文

```cpp
__identifier(C++_keyword)
```

### <a name="remarks"></a>解説

キーワードではない識別子での **__identifier** キーワードの使用は許可されていますが、スタイルの問題として、極力回避することをお勧めします。

## <a name="windows-runtime"></a>Windows ランタイム

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

### <a name="examples"></a>使用例

**例**

次の例では、C# で **template** という名前のクラスが作成され、DLL として配布されます。 **template** クラスを使用する C++/CLI プログラムでは、 **__identifier** キーワードは **template** が標準 C++ のキーワードであるという事実が隠されます。

```cs
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /ZW
#using <identifier_template.dll>
int main() {
   __identifier(template)^ pTemplate = ref new __identifier(template)();
   pTemplate->Run();
}
```

## <a name="common-language-runtime"></a>共通言語ランタイム

### <a name="remarks"></a>解説

**__identifier** キーワードは、`/clr` コンパイラ オプションで有効です。

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次の例では、C# で **template** という名前のクラスが作成され、DLL として配布されます。 **template** クラスを使用する C++/CLI プログラムでは、 **__identifier** キーワードは **template** が標準 C++ のキーワードであるという事実が隠されます。

```cs
// identifier_template.cs
// compile with: /target:library
public class template {
   public void Run() { }
}
```

```cpp
// keyword__identifier.cpp
// compile with: /clr
#using <identifier_template.dll>

int main() {
   __identifier(template) ^pTemplate = gcnew __identifier(template)();
   pTemplate->Run();
}
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)<br/>
[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)