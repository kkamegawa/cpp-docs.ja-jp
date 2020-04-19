---
title: '#using ディレクティブ (C++/cli)'
ms.date: 08/29/2019
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
ms.openlocfilehash: 5dae5c277055157aef5451c19ee020fbbd2aaccb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220197"
---
# <a name="using-directive-ccli"></a>#using ディレクティブ (C++/cli)

[/Clr](../build/reference/clr-common-language-runtime-compilation.md)でコンパイルされたプログラムにメタデータをインポートします。

## <a name="syntax"></a>構文

> **#using** *ファイル* **[as_friend]**

### <a name="parameters"></a>パラメーター

*拡張子*\
MSIL .dll、.exe、.netmodule、または .obj。例えば以下のようにします。

`#using <MyComponent.dll>`

**as_friend**\
*ファイル*内のすべての型がアクセス可能であることを指定します。 詳細については、「 [FriendC++Assemblies ()](../dotnet/friend-assemblies-cpp.md)」を参照してください。

## <a name="remarks"></a>Remarks

*ファイル*は、マネージデータとマネージコンストラクト用にインポートする Microsoft 中間言語 (MSIL) ファイルにすることができます。 .Dll ファイルにアセンブリマニフェストが含まれている場合は、マニフェストで参照されているすべての .dll がインポートされ、作成しているアセンブリはメタデータ内の*ファイル*をアセンブリ参照として一覧表示します。

*ファイル*にアセンブリが含まれていない場合 (*ファイル*がモジュールの場合)、現在の (アセンブリ) アプリケーションのモジュールからの型情報を使用しない場合は、そのモジュールがアセンブリの一部であることを示すオプションがあります。[/assemblymodule](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)を使用します。 その場合、アセンブリを参照するすべてのアプリケーションで、そのモジュール内の型を使用できます。

**#Using**を使用する代わりに、 [/fu](../build/reference/fu-name-forced-hash-using-file.md)コンパイラオプションを使用することもできます。

**#using**に渡される .exe アセンブリは、.Net Visual Studio コンパイラ (Visual Basic またはビジュアルC#など) のいずれかを使用してコンパイルする必要があります。  `/clr` でコンパイルされた .exe アセンブリからメタデータをインポートしようとすると、ファイルの読み込み例外が発生します。

> [!NOTE]
> **#Using**で参照されるコンポーネントは、コンパイル時にインポートされた別のバージョンのファイルを使用して実行できます。これにより、クライアントアプリケーションで予期しない結果が発生します。

コンパイラがアセンブリ (モジュールではありません) 内の型を認識できるようにするには、型を強制的に解決する必要があります。 これは、たとえば、型のインスタンスを定義することによって強制的に行うことができます。 コンパイラのアセンブリの型名を解決する方法は他にもあります。 たとえば、アセンブリ内の型から継承する場合、型名はコンパイラに認識されます。

[__Declspec (thread)](../cpp/thread.md)を使用したソースコードからビルドされたメタデータをインポートする場合、スレッドのセマンティクスはメタデータに保存されません。 たとえば、 **__declspec (thread)** で宣言された変数が、.NET Framework 共通言語ランタイム用に構築されたプログラムでコンパイルされ、 **#using**経由でインポートされる場合、変数に **__declspec (thread)** セマンティクスはありません。

**#Using**によって参照されるファイル内のインポートされたすべての型 (マネージとネイティブの両方) は使用できますが、コンパイラはネイティブ型を定義ではなく宣言として扱います。

`/clr` でコンパイルするときには、mscorlib.dll が自動的に参照されます。

LIBPATH 環境変数は、コンパイラが **#using**に渡されたファイル名を解決するときに検索するディレクトリを指定します。

コンパイラは、次のパスに従って参照を検索します。

- **#Using**ステートメントで指定されたパスです。

- 現在のフォルダー。

- .NET Framework のシステム ディレクトリ。

- [/Ai](../build/reference/ai-specify-metadata-directories.md)コンパイラオプションを使用して追加されたディレクトリ。

- LIBPATH 環境変数のディレクトリ。

## <a name="example"></a>例

アセンブリ (C) をビルドし、それ自体が別のアセンブリ (A) を参照するアセンブリ (B) を参照する場合、C での型のいずれかを明示的に使用しない限り、アセンブリ A を明示的に参照する必要はありません。

```cpp
// using_assembly_A.cpp
// compile with: /clr /LD
public ref class A {};
```

## <a name="example"></a>例

```cpp
// using_assembly_B.cpp
// compile with: /clr /LD
#using "using_assembly_A.dll"
public ref class B {
public:
   void Test(A a) {}
   void Test() {}
};
```

## <a name="example"></a>例

次の例では、 *using_assembly_A*で定義されている型をプログラムが使用していないため、 *using_assembly_A*を参照しない場合、コンパイラエラーは発生しません。

```cpp
// using_assembly_C.cpp
// compile with: /clr
#using "using_assembly_B.dll"
int main() {
   B b;
   b.Test();
}
```

## <a name="see-also"></a>関連項目

[プリプロセッサディレクティブ](../preprocessor/preprocessor-directives.md)
