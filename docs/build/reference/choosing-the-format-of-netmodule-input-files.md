---
title: .netmodule 入力ファイルの形式の選択
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: d48bfe84210143db333d1e6b081acf1aa66980cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294578"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>.netmodule 入力ファイルの形式の選択

MSIL の .obj ファイル (でコンパイルされた[/clr](clr-common-language-runtime-compilation.md)) .netmodule ファイルとしても使用できます。  .obj ファイルには、メタデータとネイティブのシンボルが含まれます。  .netmodule には、メタデータにはのみが含まれます。

できます/addmodule コンパイラ オプションを使用して、MSIL の .obj ファイルをその他の Visual Studio コンパイラに渡す (が .obj ファイルは、生成されたアセンブリの一部になるし、アセンブリに付属する必要がありますに注意してください)。  たとえば、Visual c# および Visual Basic には、/addmodule コンパイラ オプションがあります。

> [!NOTE]
>  ほとんどの場合は、.net モジュールを作成したコンパイルの .obj ファイルをリンカーに渡す必要があります。  .Dll または .netmodule の MSIL モジュールのファイルをリンカーに渡すと、LNK1107 可能性があります。

.obj ファイルを使用して参照するには関連付けられている .h ファイルと一緒に # ソースに include、.netmodule ファイルで、C++ アプリケーションでマネージ型のみを使用できますが、モジュール内のネイティブ型を使用する C++ アプリケーションを許可します。  .Obj ファイルをしようとした場合は、# を using ネイティブ型に関する情報は使用できません。# 代わりに include .obj ファイルの .h ファイル。

その他の Visual Studio コンパイラは、モジュールからのマネージ型のみを使用できます。

MSVC リンカーへのモジュールの入力としての .netmodule または .obj ファイルを使用するのに必要があるかどうか判断するのにには、次を使用します。

- Visual C 以外の Visual Studio コンパイラを構築している場合、.netmodule を生成およびリンカーへの入力として、.netmodule を使用します。

- MSVC コンパイラを使用してモジュールを生成し、ライブラリ以外のものをビルドするモジュールを使用する場合は、モジュール、リンカー入力として、コンパイラによって生成された .obj ファイルを使用している場合入力としての .netmodule ファイルを使わないでください。

- ネイティブ、マネージ ライブラリをビルドするモジュールを使用する場合は、リンカーへのモジュールの入力としての .obj ファイルを使用し、.lib ライブラリ ファイルを生成します。

- モジュールを使用して、マネージ ライブラリをビルドして、リンカーへのすべてのモジュール入力する場合は検証可能 (/clr:safe により生成) は、リンカーへのモジュールの入力としての .obj ファイルを使用し、(アセンブリ) .dll または .netmodule (モジュール) ライブラリのファイルを生成します。

- モジュールを使用して、マネージ ライブラリをビルドして、リンカーに 1 つまたは複数のモジュールの入力は単なる/clr で生成する場合は、リンカーへのモジュールの入力としての .obj ファイルを使用し、.dll (アセンブリ) を生成します。  ライブラリ コンポーネント モジュール (はもに送付する各モジュールの .h ファイルの .obj ファイルのライブラリでは、ライブラリからのマネージ型とする場合も、ライブラリ内のネイティブ型を使用する C++ アプリケーションを公開する場合は、、を参照できるように #include ソース コードから)。

## <a name="see-also"></a>関連項目

[.netmodule ファイル (リンカー入力)](netmodule-files-as-linker-input.md)
