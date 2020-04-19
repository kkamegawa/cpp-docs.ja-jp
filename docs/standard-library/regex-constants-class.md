---
title: regex_constants クラス
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_constants
- regex/std::regex_constants::error_collate
- regex/std::regex_constants::error_ctype
- regex/std::regex_constants::error_escape
- regex/std::regex_constants::error_backref
- regex/std::regex_constants::error_brack
- regex/std::regex_constants::error_paren
- regex/std::regex_constants::error_brace
- regex/std::regex_constants::error_badbrace
- regex/std::regex_constants::error_range
- regex/std::regex_constants::error_space
- regex/std::regex_constants::error_badrepeat
- regex/std::regex_constants::error_complexity
- regex/std::regex_constants::error_stack
- regex/std::regex_constants::error_parse
- regex/std::regex_constants::error_syntax
- regex/std::regex_constants::match_default
- regex/std::regex_constants::match_not_bol
- regex/std::regex_constants::match_not_eol
- regex/std::regex_constants::match_not_bow
- regex/std::regex_constants::match_not_eow
- regex/std::regex_constants::match_any
- regex/std::regex_constants::match_not_null
- regex/std::regex_constants::match_continuous
- regex/std::regex_constants::match_prev_avail
- regex/std::regex_constants::format_default
- regex/std::regex_constants::format_sed
- regex/std::regex_constants::format_no_copy
- regex/std::regex_constants::format_first_only
- regex/std::regex_constants::ECMAScript
- regex/std::regex_constants::basic
- regex/std::regex_constants::extended
- regex/std::regex_constants::awk
- regex/std::regex_constants::grep
- regex/std::regex_constants::egrep
- regex/std::regex_constants::icase
- regex/std::regex_constants::nosubs
- regex/std::regex_constants::optimize
- regex/std::regex_constants::collate
helpviewer_keywords:
- std::regex_constants [C++]
- std::regex_constants [C++], error_collate
- std::regex_constants [C++], error_ctype
- std::regex_constants [C++], error_escape
- std::regex_constants [C++], error_backref
- std::regex_constants [C++], error_brack
- std::regex_constants [C++], error_paren
- std::regex_constants [C++], error_brace
- std::regex_constants [C++], error_badbrace
- std::regex_constants [C++], error_range
- std::regex_constants [C++], error_space
- std::regex_constants [C++], error_badrepeat
- std::regex_constants [C++], error_complexity
- std::regex_constants [C++], error_stack
- std::regex_constants [C++], error_parse
- std::regex_constants [C++], error_syntax
- std::regex_constants [C++], match_default
- std::regex_constants [C++], match_not_bol
- std::regex_constants [C++], match_not_eol
- std::regex_constants [C++], match_not_bow
- std::regex_constants [C++], match_not_eow
- std::regex_constants [C++], match_any
- std::regex_constants [C++], match_not_null
- std::regex_constants [C++], match_continuous
- std::regex_constants [C++], match_prev_avail
- std::regex_constants [C++], format_default
- std::regex_constants [C++], format_sed
- std::regex_constants [C++], format_no_copy
- std::regex_constants [C++], format_first_only
- std::regex_constants [C++], ECMAScript
- std::regex_constants [C++], basic
- std::regex_constants [C++], extended
- std::regex_constants [C++], awk
- std::regex_constants [C++], grep
- std::regex_constants [C++], egrep
- std::regex_constants [C++], icase
- std::regex_constants [C++], nosubs
- std::regex_constants [C++], optimize
- std::regex_constants [C++], collate
ms.assetid: 4a69c0ba-c46d-46e4-bd29-6f4efb805f26
ms.openlocfilehash: c8abca8109db9c781d63721b795feb01161fdb40
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451662"
---
# <a name="regexconstants-namespace"></a>regex_constants 名前空間

正規表現フラグの名前空間です。

## <a name="syntax"></a>構文

```cpp
namespace regex_constants {
    enum syntax_option_type;
    enum match_flag_type;
    enum error_type;
}
```

## <a name="remarks"></a>Remarks

`regex_constants` 名前空間は、各種のフラグおよび関連するフラグ値をカプセル化します。

|||
|-|-|
|[error_type](#error_type)|正規表現の構文エラーを報告するためのフラグです。|
|[match_flag_type](#match_flag_type)|正規表現照合オプションのフラグ。|
|[syntax_option_type](#syntax_option_type)|構文オプションを選択するためのフラグ。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<regex>

**名前空間:** std

## <a name="error_type"></a>  regex_constants::error_type

正規表現の構文エラーを報告するためのフラグです。

```cpp
enum error_type
    {    // identify error
    error_collate,
    error_ctype,
    error_escape,
    error_backref,
    error_brack,
    error_paren,
    error_brace,
    error_badbrace,
    error_range,
    error_space,
    error_badrepeat,
    error_complexity,
    error_stack,
    error_parse,
    error_syntax
    };
```

### <a name="remarks"></a>Remarks

この型は、エラー フラグを保持できるオブジェクトを表す列挙型です。 次に、それぞれのフラグ値を示します。

`error_backref` -- 式に正しくない前方参照が存在する

`error_badbrace` -- 式が { } 式に正しくない回数を含んでいる

`error_badrepeat` -- 繰り返し式 (一般に、'*'、''、'+'、'{' のいずれか) の前に式が指定されていない

`error_brace` -- 式で '{' または '}' の対応が正しくない

`error_brack` -- 式で '[' または ']' の対応が正しくない

`error_collate` -- 式に正しくない照合要素名が存在する

`error_complexity` -- 検索式が複雑すぎるために失敗した

`error_ctype` -- 式に正しくない文字クラス名が存在する

`error_escape` -- 式に正しくないエスケープ シーケンスが存在する

`error_paren` -- 式で '(' または ')' の対応が正しくない

`error_parse` -- 式の解析に失敗した

`error_range` -- 式に正しくない文字範囲指定子が存在する

`error_space` -- リソース不足が原因で正規表現の解析に失敗した

`error_stack` -- メモリ不足が原因で検索に失敗した

`error_syntax` -- 構文エラーが原因で解析に失敗した

`error_backref` -- 式に正しくない前方参照が存在する

## <a name="match_flag_type"></a>  regex_constants::match_flag_type

正規表現照合オプションのフラグ。

```cpp
enum match_flag_type
    {    // specify matching and formatting rules
    match_default = 0x0000,
    match_not_bol = 0x0001,
    match_not_eol = 0x0002,
    match_not_bow = 0x0004,
    match_not_eow = 0x0008,
    match_any = 0x0010,
    match_not_null = 0x0020,
    match_continuous = 0x0040,
    match_prev_avail = 0x0100,
    format_default = 0x0000,
    format_sed = 0x0400,
    format_no_copy = 0x0800,
    format_first_only = 0x1000,
    _Match_not_null = 0x2000
    };
```

### <a name="remarks"></a>Remarks

この型は、テキスト シーケンスを正規表現に照らして照合するときに使用されるオプションと、テキストを置き換えるときに使用される書式設定フラグを表すビットマスク型です。 オプションは `|`を使用して連結できます。

照合オプションは次のとおりです。

`match_default`

`match_not_bol` - ターゲット シーケンス内の先頭の位置を行の始まりとして処理しません

`match_not_eol` - ターゲット シーケンス内の末尾の次の位置を行の終わりとして処理しません

`match_not_bow` - ターゲット シーケンス内の先頭の位置を単語の始まりとして処理しません

`match_not_eow` - ターゲット シーケンス内の末尾の次の位置を単語の終わりとして処理しません

`match_any` - 複数の一致が可能な場合は、すべての一致が受け入れられます

`match_not_null` - 空のサブシーケンスを一致として処理しません

`match_continuous` - ターゲット シーケンスの先頭以外で一致を検索しません

`match_prev_avail` -- `--first` は正しい反復子です。`match_not_bol` と `match_not_bow` は設定されている場合に無視されます

書式指定フラグは次のとおりです。

`format_default` -- ECMAScript 書式規則を使用します

`format_sed` -- sed 書式規則を使用します

`format_no_copy` -- 正規表現と一致しないテキストをコピーしません

`format_first_only` -- 最初の一致の後は一致を検索しません

## <a name="syntax_option_type"></a>  regex_constants::syntax_option_type

構文オプションを選択するためのフラグ。

```cpp
enum syntax_option_type
    {    // specify RE syntax rules
    ECMAScript = 0x01,
    basic = 0x02,
    extended = 0x04,
    awk = 0x08,
    grep = 0x10,
    egrep = 0x20,
    _Gmask = 0x3F,

    icase = 0x0100,
    nosubs = 0x0200,
    optimize = 0x0400,
    collate = 0x0800
    };
```

### <a name="remarks"></a>Remarks

この型は、正規表現をコンパイルするときに使用される言語指定子と構文修飾子を表すビットマスク型です。 オプションは `|`を使用して連結できます。 一度に使用できる言語指定子は 1 つだけです。

言語指定子は次のとおりです。

`ECMAScript` -- ECMAScript としてコンパイルします

`basic` -- BRE としてコンパイルします

`extended` -- ERE としてコンパイルします

`awk` -- awk としてコンパイルします

`grep` -- grep としてコンパイルします

`egrep` -- egrep としてコンパイルします

構文修飾子は次のとおりです。

`icase` -- 一致で大文字と小文字を区別しません

`nosubs` -- 実装でキャプチャ グループの内容を追跡する必要がありません

`optimize` -- 実装で正規表現のコンパイル速度よりも、照合の速度を重視する必要があります

`collate` -- 一致でロケールを区別します

## <a name="see-also"></a>関連項目

[\<regex>](../standard-library/regex.md)\
[regex_error クラス](../standard-library/regex-error-class.md)\
[\<regex > 関数](../standard-library/regex-functions.md)\
[regex_iterator クラス](../standard-library/regex-iterator-class.md)\
[\<regex > 演算子](../standard-library/regex-operators.md)\
[regex_token_iterator クラス](../standard-library/regex-token-iterator-class.md)\
[regex_traits クラス](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
