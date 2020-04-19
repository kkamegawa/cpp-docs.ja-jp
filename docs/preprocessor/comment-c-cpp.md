---
title: comment プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.comment
- comment_CPP
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
ms.openlocfilehash: 3175ad5318bcc6fd9aa6233258ccec9033c89be8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219103"
---
# <a name="comment-pragma"></a>comment プラグマ

オブジェクト ファイルまたは実行可能ファイル内にコメント レコードを配置します。

## <a name="syntax"></a>構文

> **#pragma コメント (** *コメントの種類*[ **,、** *コメント文字列*"] **)**

## <a name="remarks"></a>Remarks

*コメントの種類*は、次に示す定義済みの識別子の1つで、コメントレコードの種類を指定します。 *コメント文字列*(省略可能) は、一部のコメントの種類に関する追加情報を提供する文字列リテラルです。 *コメント文字列*は文字列リテラルなので、エスケープ文字、埋め込み引用符 (`"`)、および連結に関して、文字列リテラルのすべての規則に従います。

### <a name="compiler"></a>コンパイラ

オブジェクト ファイル内にコンパイラの名前とバージョン番号を配置します。 このコメント レコードはリンカーには無視されます。 このレコードの種類に*コメント文字列*パラメーターを指定すると、コンパイラによって警告が生成されます。

### <a name="lib"></a>lib

オブジェクト ファイル内にライブラリ検索レコードを配置します。 このコメントの種類には、リンカーが検索するライブラリの名前 (および場合によってはパス) を含む*コメント文字列*パラメーターが指定されている必要があります。 ライブラリ名は、オブジェクトファイル内の既定のライブラリ検索レコードに従います。リンカーは、 [/nodefaultlib](../build/reference/nodefaultlib-ignore-libraries.md)でライブラリが指定されていない場合に、コマンドラインで指定した場合と同じように、このライブラリを検索します。 同じソース ファイルに複数のライブラリ検索レコードを配置できます。各レコードは、ソース ファイルで見つかった順序と同じ順序でオブジェクト ファイルに出現します。

既定のライブラリと追加されたライブラリの順序が重要な場合、 [/zl](../build/reference/zl-omit-default-library-name.md)スイッチを使用してコンパイルすると、既定のライブラリ名がオブジェクトモジュールに配置されなくなります。 2 つ目の comment プラグマを使用して、追加したライブラリの後に既定のライブラリの名前を挿入することができます。 これらのプラグマを使用して指定したライブラリは、ソース コードと同じ順序でオブジェクト モジュールに出現します。

### <a name="linker"></a>リンカー

[リンカーオプション](../build/reference/linker-options.md)をオブジェクトファイルに配置します。 このコメントの種類を使用して、コマンド ラインに渡す代わりにリンカー オプションを指定するか、開発環境でリンカー オプションを指定することができます。 たとえば、/include オプションを指定して、強制的にシンボルを追加できます。

```C
#pragma comment(linker, "/include:__mySymbol")
```

リンカー識別子に渡すことができるのは、次の (*コメントの種類*) リンカーオプションだけです。

- [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)

- [/EXPORT](../build/reference/export-exports-a-function.md)

- [/INCLUDE](../build/reference/include-force-symbol-references.md)

- [/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)

- [/MERGE](../build/reference/merge-combine-sections.md)

- [/SECTION](../build/reference/section-specify-section-attributes.md)

### <a name="user"></a>ユーザー

オブジェクト ファイル内に一般的なコメントを配置します。 *コメント文字列*パラメーターには、コメントのテキストが含まれています。 このコメント レコードはリンカーには無視されます。

## <a name="examples"></a>使用例

次のプラグマを指定すると、リンカーはリンク中に EMAPI.LIB ライブラリを探します。 リンカーは、まず現在の作業ディレクトリ内を検索し、次に LIB 環境変数で指定されたパス内を検索します。

```C
#pragma comment( lib, "emapi" )
```

次のプラグマを指定すると、コンパイラはオブジェクト ファイル内にコンパイラの名前とバージョン番号を埋め込みます。

```C
#pragma comment( compiler )
```

コメント*文字列*パラメーターを受け取るコメントについては、マクロを文字列リテラルに拡張する場合に、文字列リテラルを使用する任意の場所でマクロを使用できます。 文字列リテラルと、文字列リテラルに展開されるマクロとの任意の組み合わせを連結することもできます。 たとえば、次のステートメントは許容されます。

```C
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
