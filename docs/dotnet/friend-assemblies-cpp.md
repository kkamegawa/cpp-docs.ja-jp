---
title: フレンド アセンブリ (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- friend assemblies, Visual C++
ms.assetid: 8d55fee0-b7c2-4fbe-a23b-dfe424dc71cd
ms.openlocfilehash: 05b9d8bcf5d7364e1dcd31940bc0db64a5e605f1
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447305"
---
# <a name="friend-assemblies-c"></a>フレンド アセンブリ (C++)

適用可能なランタイムは、*フレンド アセンブリ*言語機能により、名前空間スコープ、または 1 つまたは複数のクライアント アセンブリまたは .netmodule がアクセスできるアセンブリ コンポーネント内のグローバル スコープにある型です。

## <a name="all-runtimes"></a>すべてのランタイム

**解説**

(この言語機能はすべてのランタイムでないサポート)。

## <a name="windows-runtime"></a>Windows ランタイム

**解説**

(この言語機能は Windows ランタイムでないサポート)。

### <a name="requirements"></a>必要条件

コンパイラ オプション: **/ZW**

## <a name="common-language-runtime"></a>共通言語ランタイム

**解説**

#### <a name="to-make-types-at-namespace-scope-or-global-scope-in-an-assembly-component-accessible-to-a-client-assembly-or-netmodule"></a>アセンブリ コンポーネントの名前空間のスコープまたはグローバル スコープにある型にクライアント アセンブリ、または .netmodule にアクセスできるようにするには

1. コンポーネントでは、アセンブリ属性を指定<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>、クライアント アセンブリまたは名前空間スコープ、またはコンポーネント内のグローバル スコープにある型にアクセスする .netmodule の名前を渡します。  追加の属性を指定することで、複数のクライアント アセンブリまたは .netmodule を指定できます。

1. クライアント アセンブリまたはコンポーネントのアセンブリを使用して参照するときに、.netmodule `#using`、渡す、`as_friend`属性。  指定した場合、`as_friend`属性が指定されていないアセンブリを`InternalsVisibleToAttribute`、名前空間スコープ、またはコンポーネント内のグローバル スコープでの型にアクセスしようとする場合、ランタイム例外がスローされます。

アセンブリを格納している場合、ビルド エラーが発生、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>属性が厳密な名前が使用するクライアント アセンブリがない、`as_friend`属性します。

名前空間のスコープとグローバル スコープの種類は、クライアント アセンブリ、または .netmodule にわかっていますされますが、メンバーのアクセシビリティは引き続き有効です。  たとえば、プライベート メンバーにアクセスすることはできません。

アセンブリ内のすべての型へのアクセスを明示的に付与する必要があります。  たとえば、アセンブリ C がアクセスできないすべての種類にアセンブリ A でアセンブリ C がアセンブリ B を参照し、アセンブリ B はアセンブリ A のすべての型へのアクセスを持つ場合

署名する方法についてに厳密な名前を付与する方法: アセンブリは、Microsoft を使用して構築されたC++コンパイラを参照してください[厳密な名前のアセンブリ (アセンブリ署名) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。

フレンド アセンブリの機能を使用する代わりに、使用することができます<xref:System.Security.Permissions.StrongNameIdentityPermission>個々 の型へのアクセスを制限します。

### <a name="requirements"></a>必要条件

コンパイラ オプション: **/clr**

### <a name="examples"></a>使用例

次のコード例では、コンポーネントの種類にアクセスできるクライアント アセンブリを指定するコンポーネントを定義します。

```cpp
// friend_assemblies.cpp
// compile by using: /clr /LD
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type
[assembly:InternalsVisibleTo("friend_assemblies_2")];

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

次のコード例では、コンポーネントでプライベート型にアクセスします。

```cpp
// friend_assemblies_2.cpp
// compile by using: /clr
#using "friend_assemblies.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

次のコード例では、コンポーネントを定義しますが、コンポーネントの型にアクセスできるクライアント アセンブリを指定しません。

使用して、コンポーネントがリンクされていることに注意してください。 **/opt: noref**します。 これにより、コンポーネントのメタデータは、必要でない場合にプライベート型が出力されること、`InternalsVisibleTo`属性が存在します。 詳細については、次を参照してください。 [/OPT (最適化)](../build/reference/opt-optimizations.md)します。

```cpp
// friend_assemblies_3.cpp
// compile by using: /clr /LD /link /opt:noref
using namespace System;

ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

次のコード例では、そのプライベート型にアクセス権を与えられませんコンポーネントにプライベート型にアクセスしようとするクライアントを定義します。 ランタイムの動作のため、例外をキャッチする場合、ヘルパー関数でプライベート型にアクセスする必要がありますましょう。

```cpp
// friend_assemblies_4.cpp
// compile by using: /clr
#using "friend_assemblies_3.dll" as_friend
using namespace System;

void Test() {
   Class1 ^ a = gcnew Class1;
}

int main() {
   // to catch this kind of exception, use a helper function
   try {
      Test();
   }
   catch(MethodAccessException ^ e) {
      Console::WriteLine("caught an exception");
   }
}
```

```Output
caught an exception
```

次のコード例では、コンポーネントの型にアクセスできるクライアント アセンブリを指定する厳密な名前のコンポーネントを作成する方法を示します。

```cpp
// friend_assemblies_5.cpp
// compile by using: /clr /LD /link /keyfile:friend_assemblies.snk
using namespace System::Runtime::CompilerServices;
using namespace System;
// an assembly attribute, not bound to a type

[assembly:InternalsVisibleTo("friend_assemblies_6, PublicKey=00240000048000009400000006020000002400005253413100040000010001000bf45d77fd991f3bff0ef51af48a12d35699e04616f27ba561195a69ebd3449c345389dc9603d65be8cd1987bc7ea48bdda35ac7d57d3d82c666b7fc1a5b79836d139ef0ac8c4e715434211660f481612771a9f7059b9b742c3d8af00e01716ed4b872e6f1be0e94863eb5745224f0deaba5b137624d7049b6f2d87fba639fc5")];

private ref class Class1 {
public:
   void Test_Public() {
      Console::WriteLine("Class1::Test_Public");
   }
};
```

コンポーネントがその公開キーを指定する必要がありますに注意してください。 次のコマンド キーのペアを作成し、公開キーを取得するコマンド プロンプトで、順番に実行することをお勧めします。

**sn -d friend_assemblies.snk**

**sn -k friend_assemblies.snk**

**sn -i friend_assemblies.snk friend_assemblies.snk**

**sn -pc friend_assemblies.snk key.publickey**

**sn-tp key.publickey**

次のコード例では、厳密な名前のコンポーネントでプライベート型にアクセスします。

```cpp
// friend_assemblies_6.cpp
// compile by using: /clr /link /keyfile:friend_assemblies.snk
#using "friend_assemblies_5.dll" as_friend

int main() {
   Class1 ^ a = gcnew Class1;
   a->Test_Public();
}
```

```Output
Class1::Test_Public
```

## <a name="see-also"></a>関連項目

[ランタイム プラットフォームのコンポーネントの拡張機能](../extensions/component-extensions-for-runtime-platforms.md)
