---
title: MSVC リンカーの参照
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 3a9eebef0a264b0131311b5ca96011a4d56264a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176630"
---
# <a name="linking"></a>リンク

C++ プロジェクトで、*リンク*コンパイラがオブジェクト ファイル (*.obj) にソース コードをコンパイル後の手順が実行されます。 リンカー (link.exe) は、1 つの実行可能ファイルにオブジェクト ファイルを結合します。 

Visual Studio の内外で、リンカー オプションを設定できます。 Visual Studio 内でプロジェクト ノードを右クリックしてリンカー オプションにアクセスする**ソリューション エクスプ ローラー**を選択して**プロパティ**プロパティ ページを表示します。 選択**リンカー**で左側のウィンドウで、ノードを展開し、すべてのオプションを参照してください。 


## <a name="linker-command-line-syntax"></a>リンカー コマンドラインの構文

Visual Studio の外部リンクを実行する場合は、1 つまたは複数の方法で入力を指定できます。

- コマンド ライン

- コマンド ファイルを使用します。

- 環境変数

その後にオプションおよびコマンド ファイル、コマンドラインで指定された順序で、リンクの環境変数でリンク最初プロセス オプションを指定します。 オプションは引数を繰り返し、処理された最後の 1 つが優先されます。

オプションは、すべてのビルドに適用されます。特定の入力ファイルをオプションを適用しないことができます。

リンクを実行します。実行可能ファイルを次のコマンド構文を使用します。

```
LINK arguments
```

`arguments`オプションとファイル名を含めるし、任意の順序で指定することができます。 オプションは、処理された最初の場合は、次のファイルです。 引数を区切るためには、1 つ以上のスペースまたはタブを使用します。

> [!NOTE]
>  このツールは、Visual Studio コマンド プロンプトからのみ開始できます。 システム コマンド プロンプトやエクスプローラーからは開始できません。

## <a name="command-line"></a>コマンド ライン

オプションの指定子のコマンドラインでオプションがで構成されています。 ダッシュ (-) またはスラッシュ (/) のいずれかの後に、オプションの名前。 オプション名の省略形は使用できません。 いくつかのオプションは、コロン (:) 後に指定された引数を取る。 スペースまたはタブは許可されませんオプションの指定を除く/COMMENT オプションでは、引用符で囲まれた文字列内にあります。 10 進数または C 言語表記で数値の引数を指定します。 オプション名および関連するキーワードまたはファイル名引数は大文字小文字が区別されませんが、引数としての識別子が大文字小文字を区別します。

ファイルをリンカーに渡すするには、リンク コマンドの後に、コマンドラインで、ファイル名を指定します。 ファイル名は、絶対または相対パスを指定して、ファイル名にワイルドカードを使用することができます。 ドット (.) とファイル名拡張子を省略すると、リンク ファイルの .obj と見なされます。 リンクやを使用しないファイル名拡張子がないことにファイルの内容に関する判断を行う調べて、ファイルの種類を決定し、それに応じて処理します。

link.exe は、成功 (エラーなし)、0 を返します。  それ以外の場合、リンカーは、リンクを停止するエラー番号を返します。  たとえば、リンカーは、LNK1104 を生成、リンカーは 1104 を返します。  したがって、エラーが発生、リンカーによって返される最小のエラー番号には 1000 です。  128 の戻り値は、オペレーティング システムまたは .config ファイルのいずれかの構成に問題を表しますlink.exe または c2.dll、ローダーは読み込まれませんでした。

## <a name="link-command-files"></a>LINK コマンド ファイル

コマンド ファイルの形式でリンクには、コマンドライン引数を渡すことができます。 リンカーにコマンド ファイルを指定するには、次の構文を使用します。

> **リンク\@**  <em>commandfile</em>

*Commandfile*テキスト ファイルの名前を指定します。 スペースまたはタブ間は入れません、アット マーク (**\@**) とファイル名。 既定の拡張機能はありません。任意の拡張子を含む完全なファイル名を指定する必要があります。 ワイルドカードを使用することはできません。 ファイル名では、絶対または相対パスを指定できます。 リンクは、ファイルを検索する環境変数を使用しません。

コマンド ファイルで引数で分離できるスペースまたはタブ (コマンドライン) のように、改行文字。

コマンド ファイルでは、コマンドラインの一部またはすべてを指定できます。 LINK コマンドでは、複数のコマンド ファイルを使用することができます。 リンクは、コマンドラインでその場所に指定されたものかのように、コマンド ファイルの入力を受け入れます。 コマンド ファイルを入れ子にすることはできません。 リンクが、コマンド ファイルの内容をエコーしない限り、 [/NOLOGO](nologo-suppress-startup-banner-linker.md)オプションを指定します。

## <a name="example"></a>例

DLL をビルドするには、次のコマンドは、独立したコマンドのファイルにオブジェクト ファイルとライブラリの名前を渡し、3 番目のコマンド/EXPORTS オプションの指定のファイルを使用します。

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>環境変数 LINK

LINK ツールでは、次の環境変数を使用します。

- リンクと\_リンク\_、定義されている場合。 定義されている引数およびリンク ツール オプションと環境変数 LINK に定義されている引数の前に付加し、オプションを追加します、\_リンク\_環境変数を処理する前にコマンドライン引数。

- LIB。定義されている場合。 LINK ツールは、オブジェクト、ライブラリ、またはコマンドラインでまたはを指定されたその他のファイルを検索するときに LIB パスを使用、 [/base](base-base-address.md)オプション。 また、オブジェクトで指定された .pdb ファイルを検索するときにも LIB パスを使用します。 LIB 変数では、複数のパスをセミコロンで区切って指定できます。 1 つのパスは Visual C++ インストールの \lib サブディレクトリを示す必要があります。

- PATH。ツールが CVTRES を実行する必要があり、LINK 自身と同じディレクトリ内にこのファイルが見つからない場合  (LINK では、.res ファイルをリンクするために CVTRES を必要とします)。PATH は Visual C++ インストールの \bin サブディレクトリを示す必要があります。

- TMP。OMF ファイルまたは .res ファイルをリンクするときのディレクトリを指定します。

## <a name="see-also"></a>関連項目

[C/C++ ビルドのリファレンス](c-cpp-building-reference.md)
[MSVC リンカー オプション](linker-options.md)
[モジュール定義 (.def) ファイル](module-definition-dot-def-files.md)
[リンカー サポートDll の遅延読み込み](linker-support-for-delay-loaded-dlls.md)
