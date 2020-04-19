---
title: /clr (共通言語ランタイムのコンパイル)
ms.date: 05/16/2019
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
ms.openlocfilehash: fa2be3d3ce17df104cda121e4869c975ec6dd440
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837304"
---
# <a name="clr-common-language-runtime-compilation"></a>/clr (共通言語ランタイムのコンパイル)

アプリケーションおよびコンポーネントで、共通言語ランタイム (CLR) の機能を使用できるようにします。

## <a name="syntax"></a>構文

> **/clr**[ **:** _options_]

## <a name="arguments"></a>引数

*options*<br/>
次の 1 つまたは複数のスイッチをコンマで区切って指定します。

- none

   オプションを指定しない場合、 **/clr** によってアプリケーションのメタデータが作成されます。 このメタデータは、他の CLR アプリケーションで使用できます。また、このメタデータによって、他の CLR コンポーネントのメタデータの型とデータをアプリケーションで使用できるようになります。 「[混在 (ネイティブおよびマネージド) アセンブリ](../../dotnet/mixed-native-and-managed-assemblies.md)」を参照してください。

- **pure**

   **/clr:pure の使用は非推奨とされます**。 このオプションは、Visual Studio 2017 以降で削除されます。 純粋 MSIL にする必要があるコードは、C# に移植することをお勧めします。

- **safe**

   **/clr:safe は非推奨とされます**。 このオプションは、Visual Studio 2017 以降で削除されます。 安全 MSIL にする必要があるコードは、C# に移植することをお勧めします。

- **noAssembly**

   **/clr:noAssembly は非推奨とされます**。 代わりに、 [/LN (Create MSIL Module)](ln-create-msil-module.md) を使用してください。

   アセンブリ マニフェストを出力ファイルに挿入できないことを指定します。 既定では、 **noAssembly** オプションはオフです。

   マニフェストにアセンブリ メタデータがないマネージド プログラムを、 *モジュール*と呼びます。 **noAssembly** オプションは、モジュールを生成するときのみ使用できます。 [/c](c-compile-without-linking.md) と **/clr:noAssembly**を使用してコンパイルする場合は、リンカーのフェーズで [/NOASSEMBLY](noassembly-create-a-msil-module.md) オプションを指定してモジュールを作成します。

   Visual Studio 2005 より前のバージョンでは、 **/clr:noAssembly** には **/LD** が必要です。 現在は、 **/LD** を指定すると **/LD**が暗黙的に指定されるようになっています。

- **initialAppDomain**

   Visual C++ アプリケーションを CLR の Version 1 で実行できるようにします。  CLR の Version 1 では ASP.NET をサポートしていないため、 **initialAppDomain** を使用してコンパイルされたアプリケーションは、ASP.NET を使用しているアプリケーションでは使用しないでください。

- **nostdlib**

   既定の \clr ディレクトリを無視するようにコンパイラに指示します。 System.dll などの DLL の複数のバージョンを含めると、コンパイラはエラーを生成します。 このオプションを使用すると、コンパイル時に使用する特定のフレームワークを指定できます。

## <a name="remarks"></a>解説

マネージド コードは、CLR によって検査および管理できるコードです。 マネージド コードはマネージド オブジェクトにアクセスできます。 詳細については、「 [/clr Restrictions](clr-restrictions.md)」を参照してください。

マネージド型を定義および使用するアプリケーションの開発方法については、「 [Component Extensions for Runtime Platforms](../../extensions/component-extensions-for-runtime-platforms.md)。

**/clr** を使用してコンパイルされたアプリケーションには、マネージド データがある場合とない場合があります。

マネージド アプリケーションでのデバッグを有効にするには、「[/ASSEMBLYDEBUG (DebuggableAttribute の追加)](assemblydebug-add-debuggableattribute.md)」を参照してください。

ガベージ コレクトされたヒープでインスタンス化されるのは CLR 型のみです。 詳細については、「[クラスと構造体](../../extensions/classes-and-structs-cpp-component-extensions.md)」を参照してください。 関数をネイティブ コードにコンパイルするには、 `unmanaged` プラグマを使用します。 詳細については、「[マネージド、アンマネージド](../../preprocessor/managed-unmanaged.md)」を参照してください。

既定では、 **/clr** は無効です。 **/clr** が有効な場合は **/MD** も有効です。 詳細については、「[/MD、/MT、/LD (ランタイム ライブラリの使用)](md-mt-ld-use-run-time-library.md)」を参照してください。 **/MD** を使用すると、動的にリンクされるマルチスレッド バージョンのランタイム ルーチンが標準ヘッダー (.h) ファイルから選択されるようになります。 マネージド プログラミングでマルチスレッドが必要なのは、CLR のガベージ コレクターが、補助スレッドでファイナライザーを実行するためです。

**/c** を使用してコンパイルする場合は、[/CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md) を使用して、結果として出力されるファイルの CLR 型を指定できます。

**/clr** は **/EHa**を暗黙的に指定するため、 **/clr** では他の **/EH**オプションを指定できません。 詳細については、「[/EH (例外処理モデル)](eh-exception-handling-model.md)」を参照してください。

ファイルの CLR イメージのタイプを判断する方法については、「 [/CLRHEADER](clrheader.md)」を参照してください。

リンカーの特定の呼び出しに渡されるすべてのモジュールは、同じランタイム ライブラリ コンパイラ オプション ( **/MD** または **/LD**) を使用してコンパイルされている必要があります。

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) リンカー オプションを使用して、アセンブリにリソースを埋め込みます。 [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)、 [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)、および [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) の各リンカー オプションでも、アセンブリの作成方法をカスタマイズできます。

**/clr** が使用されるときは、 `_MANAGED` シンボルは 1 に定義されます。 詳細については、「 [Predefined Macros](../../preprocessor/predefined-macros.md)」を参照してください。

最初にネイティブなオブジェクト ファイルのグローバル変数が (実行可能ファイルが DLL の場合は DllMain の実行中に) 初期化され、その後でマネージド セクションのグローバル変数が (いずれかのマネージド コードが実行される前に) 初期化されます。 `#pragma` [init_seg](../../preprocessor/init-seg.md) は、マネージド カテゴリ内およびアンマネージド カテゴリ内での初期化の順序にのみ影響を与えます。

## <a name="metadata-and-unnamed-classes"></a>メタデータと名前のないクラス

名前のないクラスは、メタデータに `$UnnamedClass$`*crc-of-current-file-name*`$`*index*`$`のような名前で表示されます。この *index* は、コンパイル時に名前のないクラスに与えられる連続番号です。 次のコードの例では、名前のないクラスをメタデータに生成します。

```cpp
// clr_unnamed_class.cpp
// compile by using: /clr /LD
class {} x;
```

メタデータを表示するには、ildasm.exe を使用します。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
