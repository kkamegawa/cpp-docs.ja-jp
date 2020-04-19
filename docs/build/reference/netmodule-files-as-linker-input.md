---
title: に渡します。netmodule リンカー入力としてのファイル
description: Mixed を使用する方法について説明します。obj そして。netmodule .NET アセンブリを作成するときのリンカー入力としてのファイル。
ms.date: 01/30/2020
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodule files
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
no-loc:
- obj
- netmodule
- clr
- pure
- safe
ms.openlocfilehash: 83eab25624bdb81ba9191e4efe6a774551502ee0
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912825"
---
# <a name="opno-locnetmodule-files-as-linker-input"></a>に渡します。netmodule リンカー入力としてのファイル

convert.exe は、入力として MSIL *`.obj`* および *`.netmodule`* ファイルを受け入れます。 リンカーによって生成される出力ファイルは、アセンブリまたは *`.netmodule`* ファイルで、リンカーに入力された *`.obj`* または *`.netmodule`* ファイルには実行時の依存関係がありません。

## <a name="remarks"></a>Remarks

*`.netmodule`* ファイルは、/LN を使用した MSVC コンパイラ[(Msil モジュールの作成)](ln-create-msil-module.md)またはリンカー [(msil モジュールの作成)](noassembly-create-a-msil-module.md)で作成されます。 *`.obj`* ファイルは常にC++コンパイル時に作成されます。 他の Visual Studio コンパイラの場合は、 **/target:module** コンパイラ オプションを使用します。

リンカーには、 *`.netmodule`* を作成したC++コンパイルから`.obj`ファイルを渡す必要があります。 **/clr:pure** および **/clr:safe** コンパイラオプションは visual studio 2015 で非推奨とされており、visual studio 2017 以降ではサポートされていないため、 *`.netmodule`* を渡すことはサポートされなくなりました。

コマンドラインからリンカーを呼び出す方法については、「[リンカーコマンドライン構文](linking.md)」、「コマンド[ラインからの MSVC ツールセットの使用](../building-on-the-command-line.md)」、および「[コマンドラインビルドのパスと環境変数の設定](../setting-the-path-and-environment-variables-for-command-line-builds.md)」を参照してください。

**/clr** を使用して MSVC コンパイラによってコンパイルされたリンカーに *`.netmodule`* または *`.dll`* ファイルを渡すと、リンカーエラーが発生する可能性があります。 詳細については、「 [netmodule 入力ファイルの形式の選択](choosing-the-format-of-netmodule-input-files.md)」を参照してください。

リンカーは **/clr** でコンパイルされたネイティブ *`.obj`* ファイルと MSIL *`.obj`* ファイルの両方を受け入れます。 混合 *`.obj`* ファイルは、同じビルドに渡すことができます。 生成される出力ファイルの既定の検証可能性は、最小入力モジュールの検証可能性と同じです。

1つのアセンブリに含まれる2つ以上のアセンブリで構成されるアプリケーションを変更できます。 アセンブリのソースを再コンパイルし、 *`.obj`* ファイルまたは *`.netmodule`* ファイルをリンクして、1つのアセンブリを生成します。

実行可能イメージを作成するときに、 [/entry (エントリポイントシンボル)](entry-entry-point-symbol.md)を使用してエントリポイントを指定します。

MSIL *`.obj`* または *`.netmodule`* ファイルとリンクする場合は、 [/ltcg (リンク時のコード生成)](ltcg-link-time-code-generation.md)を使用します。それ以外の場合は、リンカーが msil *`.obj`* または *`.netmodule`* を検出すると、 **/ltcg**でリンクが再起動されます。 リンクが再起動していることを示す情報メッセージが表示されます。 このメッセージは無視してもかまいませんが、リンカーのパフォーマンスを向上させるには、 **/ltcg**を明示的に指定します。

MSIL *`.obj`* または *`.netmodule`* ファイルを cl.exe に渡すこともできます。

入力 MSIL *`.obj`* または *`.netmodule`* ファイルには、埋め込みリソースを含めることができません。 [/Assemblyresource (マネージリソースの埋め込み)](assemblyresource-embed-a-managed-resource.md)リンカーオプションを使用して、出力モジュールまたはアセンブリファイルにリソースを埋め込みます。 または、他の Visual Studio コンパイラで **/resource**コンパイラオプションを使用します。

## <a name="examples"></a>使用例

コードC++では、対応する **`try`** の **`catch`** ブロックが`System` 以外の例外に対して呼び出されます。 ただし、既定では、CLR は <xref:System.Runtime.CompilerServices.RuntimeWrappedException>で`System` 以外の例外をラップします。 アセンブリがC++ C++モジュールと非モジュールから作成され、 **`try`** ブロックが`System` 以外の例外をスローしたときに、対応するC++ **`try`** 句からコード内のC++ **`catch`** ブロックを呼び出す必要がある場合は、非モジュールのソースコードに `[assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)]` 属性を追加する必要があります。

```cpp
// MSIL_linking.cpp
// compile with: /c /clr
value struct V {};

ref struct MCPP {
   static void Test() {
      try {
         throw (gcnew V);
      }
      catch (V ^) {
         System::Console::WriteLine("caught non System exception in C++ source code file");
      }
   }
};

/*
int main() {
   MCPP::Test();
}
*/
```

`WrapNonExceptionThrows` 属性の `Boolean` 値を変更することにより、 C++コードの`System` ない例外をキャッチする機能を変更します。

```csharp
// MSIL_linking_2.cs
// compile with: /target:module /addmodule:MSIL_linking.obj
// post-build command: link /LTCG MSIL_linking.obj MSIL_linking_2.netmodule /entry:MLinkTest.Main /out:MSIL_linking_2.exe /subsystem:console
using System.Runtime.CompilerServices;

// enable non System exceptions
[assembly:RuntimeCompatibility(WrapNonExceptionThrows=false)]

class MLinkTest {
   public static void Main() {
      try {
         MCPP.Test();
      }
      catch (RuntimeWrappedException) {
         System.Console.WriteLine("caught a wrapped exception in C#");
      }
   }
}
```

```Output
caught non System exception in C++ source code file
```

## <a name="see-also"></a>関連項目

- [LINK の入力ファイル](link-input-files.md)
- [MSVC リンカー オプション](linker-options.md)
