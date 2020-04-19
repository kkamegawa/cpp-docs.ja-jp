---
title: リンカー ツールの警告 LNK4227
ms.date: 11/04/2016
f1_keywords:
- LNK4227
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
ms.openlocfilehash: fb657719c69445ce23d36ccf04ac4a14db0955e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352743"
---
# <a name="linker-tools-warning-lnk4227"></a>リンカー ツールの警告 LNK4227

> メタデータ演算警告 (*HRESULT*): *warning_message*

リンカーでは、マージするときに、メタデータの違いが検出されました。

- 現在ビルドされているアセンブリでの 1 つ以上の参照先のアセンブリ。

- 1 つまたは複数ソース コード ファイルをコンパイルします。

2 つのグローバル関数で同じ名前が異なる方法で宣言されたパラメーター情報がある場合に LNK4227 がなど発生する可能性があります (つまり、宣言で一貫していないすべてのコンパイル単位)。 /TEXT ildasm.exe を使用して、/METADATA *object_file* 各 .obj ファイルを型の違いを参照してください。

LNK4227 も、別のツールで発生した問題の報告に使用されます。 詳細については、警告メッセージを検索します。

警告を解決するのには、メタデータの問題を修正する必要があります。

## <a name="example"></a>例

参照アセンブリが参照するアセンブリとは異なる署名されたときに、LNK4227 が生成されます。

次の例では、LNK4227 が生成されます。

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

それから

```cpp
// LNK4227b.cpp
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe
using namespace System::Reflection;
using namespace System::Runtime::CompilerServices;

[assembly:AssemblyDelaySignAttribute(true)];
// Try the following line instead
// [assembly:AssemblyDelaySignAttribute(false)];

ref class MyClass
{
};
```

## <a name="example"></a>例

間違った形式のバージョン番号は、アセンブリの属性に渡されるときに、LNK4227 を生成こともできます。  ' *' に固有の表記法、`AssemblyVersionAttribute`します。  この警告を解決するには、使用してのみ内の数値のバージョン属性以外の`AssemblyVersionAttribute`します。

次の例では、LNK4227 が生成されます。

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```