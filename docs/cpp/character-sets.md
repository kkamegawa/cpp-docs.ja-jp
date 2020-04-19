---
title: トークンと文字セット
ms.date: 12/10/2019
helpviewer_keywords:
- Tokens (C++)
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
ms.openlocfilehash: 1f6dbe2faa6348d61ec00b411cc35e8ef5ceb57a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301614"
---
# <a name="tokens-and-character-sets"></a>トークンと文字セット

C++プログラムのテキストは、トークンと*空白*で構成されます。 トークンは、コンパイラにとって意味がある、C ++ プログラムの最小要素です。 パーサー C++は、次の種類のトークンを認識します。

- [キーワード](../cpp/keywords-cpp.md)
- [識別子](../cpp/identifiers-cpp.md)
- [数値、ブール値、およびポインターのリテラル](../cpp/numeric-boolean-and-pointer-literals-cpp.md)
- [文字列リテラルと文字リテラル](../cpp/string-and-character-literals-cpp.md)
- [ユーザー定義リテラル](../cpp/user-defined-literals-cpp.md)
- [演算子](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
- [区切り記号](../cpp/punctuators-cpp.md)

トークンは通常、空白で区切られます。1つ以上の*文字*を指定できます。

- 空白
- 水平または垂直タブ
- 改行
- フォームフィード
- コメント

## <a name="basic-source-character-set"></a>基本ソース文字セット

標準C++では、ソースファイルで使用できる*基本ソース文字セット*が指定されています。 このセットに含まれない文字を表す場合は、 *ユニバーサル文字名*を使用すると追加の文字を指定できます。 MSVC 実装では、追加の文字を使用できます。 *基本ソース文字セット*は、ソースファイルで使用される96文字で構成されます。 この文字セットには、空白文字、水平タブ、垂直タブ、フォーム フィードおよび改行の制御文字と、このセットのグラフィック文字が含まれます。

`a b c d e f g h i j k l m n o p q r s t u v w x y z`

`A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`

`0 1 2 3 4 5 6 7 8 9`

`_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`

**Microsoft 固有の仕様**

MSVC には、基本ソース文字セットのメンバーとして `$` 文字が含まれています。 また、MSVC では、ファイルのエンコードに基づいて、ソースファイルで追加の文字セットを使用することもできます。 既定では、Visual Studio は既定のコードページを使用して、ソース ファイルを保存します。 ロケール固有のコードページまたは Unicode コードページを使用してソースファイルを保存する場合、MSVC では、基本ソース文字セットで明示的に許可されていない制御コードを除き、ソースコード内でそのコードページの任意の文字を使用できます。 たとえば、日本語コードページを使用してファイルを保存すれば、コメントや識別子、文字列リテラルを日本語の文字で記述できます。 MSVC では、有効なマルチバイト文字または Unicode コードポイントに変換できない文字シーケンスは許可されません。 コンパイラ オプションによっては、一部の文字が識別子に使用できなくなることがあります。 詳細については、「 [Identifiers](../cpp/identifiers-cpp.md)」を参照してください。

**END Microsoft 固有の仕様**

### <a name="universal-character-names"></a>ユニバーサル文字名

C++ プログラムでは、基本ソース文字セットで規定されている文字よりも多くの文字を使用できます。それらの文字は、 *ユニバーサル文字名*を使用して移植可能な方法で指定します。 ユニバーサル文字名は、Unicode コード ポイントを表す文字のシーケンスで構成されます。  これには 2 つの形式があります。 `\UNNNNNNNN` は、U+NNNNNNNN 形式の Unicode コード ポイントを表すために使用します。この NNNNNNNN は、8 桁の 16 進コード ポイント番号です。 4 桁の `\uNNNN` は、U+0000NNNN 形式の Unicode コード ポイントを表すために使用します。

ユニバーサル文字名は、識別子、文字列リテラルおよび文字リテラルに使用できます。 ユニバーサル文字名を使用して、0xD800 から 0xDFFF の範囲に含まれるサロゲート コード ポイントを表すことはできません。 その代わりに、目的とするコード ポイントを使用してください。コンパイラは、必要なサロゲートを自動的に生成します。 識別子に使用できるユニバーサル文字名には、その他の制限が適用されます。 詳細については、「 [Identifiers](../cpp/identifiers-cpp.md) 」および「 [String and Character Literals](../cpp/string-and-character-literals-cpp.md)」を参照してください。

**Microsoft 固有の仕様**

Microsoft C++コンパイラは、ユニバーサル文字名形式の文字とリテラル形式の文字を同義として扱います。 たとえば、次に示すように、ユニバーサル文字名を使用して宣言した識別子がリテラル形式で使用できます。

```cpp
auto \u30AD = 42; // \u30AD is 'キ'
if (キ == 42) return true; // \u30AD and キ are the same to the compiler
```

Windows クリップボードでの拡張文字の形式は、アプリケーションのロケール設定によって決まります。 こうした文字を別のアプリケーションから切り取って、コードに貼り付けると、予期しない文字のエンコーディングが発生することがあります。 これは、コードの外見には現れない解析エラーの発生につながります。 拡張文字を貼り付ける前に、ソース ファイルのエンコーディングを Unicode コードページに設定するようにしてください。 また、拡張文字の生成には、IME または文字コード表アプリを使用するようにしてください。

**END Microsoft 固有の仕様**

### <a name="execution-character-sets"></a>実行文字セット

*実行文字セット*は、コンパイルされたプログラムで使用できる文字と文字列を表します。 これらの文字セットは、ソースファイルで許可されているすべての文字と、アラート、バックスペース、復帰、および null 文字を表す制御文字で構成されます。 実行文字セットには、ロケール固有の表現があります。
