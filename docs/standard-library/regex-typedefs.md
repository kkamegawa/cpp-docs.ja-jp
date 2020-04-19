---
title: '&lt;regex&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- regex/std::cmatch
- regex/std::cregex_iterator
- regex/std::cregex_token_iterator
- regex/std::csub_match
- regex/std::regex
- regex/std::smatch
- regex/std::sregex_iterator
- regex/std::sregex_token_iterator
- regex/std::ssub_match
- regex/std::wcmatch
- regex/std::wcregex_iterator
- regex/std::wcregex_token_iterator
- regex/std::wcsub_match
- regex/std::wregex
- regex/std::wsmatch
- regex/std::wsregex_iterator
- regex/std::wsregex_token_iterator
- regex/std::wssub_match
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
ms.openlocfilehash: 4321d9ea6fd9ba57074b25e084553fe1f0846213
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689025"
---
# <a name="ltregexgt-typedefs"></a>&lt;regex&gt; typedefs

||||
|-|-|-|
|[cmatch](#cmatch)|[cregex_iterator](#cregex_iterator)|[cregex_token_iterator](#cregex_token_iterator)|
|[csub_match](#csub_match)|[regex](#regex)|[smatch](#smatch)|
|[sregex_iterator](#sregex_iterator)|[sregex_token_iterator](#sregex_token_iterator)|[ssub_match](#ssub_match)|
|[wcmatch](#wcmatch)|[wcregex_iterator](#wcregex_iterator)|[wcregex_token_iterator](#wcregex_token_iterator)|
|[wcsub_match](#wcsub_match)|[wregex](#wregex)|[wsmatch](#wsmatch)|
|[wsregex_iterator](#wsregex_iterator)|[wsregex_token_iterator](#wsregex_token_iterator)|[wssub_match](#wssub_match)|

## <a name="cmatch"></a>  cmatch Typedef

char match_results の型定義です。

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>Remarks

この型は `const char*` 型の反復子に対して特殊化されたクラステンプレート[Match_results クラス](../standard-library/match-results-class.md)を表します。

## <a name="cregex_iterator"></a>  cregex_iterator Typedef

char regex_iterator の型定義。

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>Remarks

この型は `const char*` 型の反復子に対して特殊化されたクラステンプレート[Regex_iterator クラス](../standard-library/regex-iterator-class.md)を表します。

## <a name="cregex_token_iterator"></a>  cregex_token_iterator Typedef

char regex_token_iterator の型定義

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>Remarks

この型は `const char*` 型の反復子に対して特殊化されたクラステンプレート[Regex_token_iterator クラス](../standard-library/regex-token-iterator-class.md)を表します。

## <a name="csub_match"></a>  csub_match Typedef

char sub_match の型定義です。

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>Remarks

この型は `const char*` 型の反復子に対して特殊化されたクラステンプレート[Sub_match クラス](../standard-library/sub-match-class.md)を表します。

## <a name="regex"></a>  regex Typedef

char basic_regex の型定義です。

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>Remarks

この型は、 **char**型の要素に対するクラステンプレート[basic_regex クラス](../standard-library/basic-regex-class.md)の特殊化を表します。

> [!NOTE]
> ハイビット文字は、`regex` を使用すると予測できない結果を起こします。 0 から 127 の範囲を外れる値を使用すると未定義の動作をすることがあります。

## <a name="smatch"></a>  smatch Typedef

string match_results の型定義です。

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>Remarks

この型は `string::const_iterator` 型の反復子に対して特殊化されたクラステンプレート[Match_results クラス](../standard-library/match-results-class.md)を表します。

## <a name="sregex_iterator"></a>  sregex_iterator Typedef

文字列 regex_iterator  の型定義です。

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>Remarks

この型は `string::const_iterator` 型の反復子に対して特殊化されたクラステンプレート[Regex_iterator クラス](../standard-library/regex-iterator-class.md)を表します。

## <a name="sregex_token_iterator"></a>  sregex_token_iterator Typedef

文字列 regex_token_iterator の型定義です。

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>Remarks

この型は `string::const_iterator` 型の反復子に対して特殊化されたクラステンプレート[Regex_token_iterator クラス](../standard-library/regex-token-iterator-class.md)を表します。

## <a name="ssub_match"></a>  ssub_match Typedef

string sub_match の型定義です。

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>Remarks

この型は `string::const_iterator` 型の反復子に対して特殊化されたクラステンプレート[Sub_match クラス](../standard-library/sub-match-class.md)を表します。

## <a name="wcmatch"></a>  wcmatch Typedef

wchar_t match_results の型定義です。

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>Remarks

この型は `const wchar_t*` 型の反復子に対して特殊化されたクラステンプレート[Match_results クラス](../standard-library/match-results-class.md)を表します。

## <a name="wcregex_iterator"></a>  wcregex_iterator Typedef

wchar_t regex_iterator の型定義です。

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>Remarks

この型は `const wchar_t*` 型の反復子に対して特殊化されたクラステンプレート[Regex_iterator クラス](../standard-library/regex-iterator-class.md)を表します。

## <a name="wcregex_token_iterator"></a>  wcregex_token_iterator Typedef

wchar_t regex_token_iterator の型定義です。

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>Remarks

この型は `const wchar_t*` 型の反復子に対して特殊化されたクラステンプレート[Regex_token_iterator クラス](../standard-library/regex-token-iterator-class.md)を表します。

## <a name="wcsub_match"></a>  wcsub_match Typedef

wchar_t sub_match の型定義です。

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>Remarks

この型は `const wchar_t*` 型の反復子に対して特殊化されたクラステンプレート[Sub_match クラス](../standard-library/sub-match-class.md)を表します。

## <a name="wregex"></a>  wregex Typedef

wchar_t basic_regex の型定義です。

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>Remarks

この型は、 **wchar_t**型の要素のクラステンプレート[basic_regex クラス](../standard-library/basic-regex-class.md)の特殊化を表します。

## <a name="wsmatch"></a>  wsmatch Typedef

wstring match_results の型定義です。

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>Remarks

この型は `wstring::const_iterator` 型の反復子に対して特殊化されたクラステンプレート[Match_results クラス](../standard-library/match-results-class.md)を表します。

## <a name="wsregex_iterator"></a>  wsregex_iterator Typedef

wstring regex_iterator の型定義です。

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>Remarks

この型は `wstring::const_iterator` 型の反復子に対して特殊化されたクラステンプレート[Regex_iterator クラス](../standard-library/regex-iterator-class.md)を表します。

## <a name="wsregex_token_iterator"></a>  wsregex_token_iterator Typedef

wstring regex_token_iterator の型定義です。

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>Remarks

この型は `wstring::const_iterator` 型の反復子に対して特殊化されたクラステンプレート[Regex_token_iterator クラス](../standard-library/regex-token-iterator-class.md)を表します。

## <a name="wssub_match"></a>  wssub_match Typedef

Wstring sub_match の型定義です。

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>Remarks

この型は `wstring::const_iterator` 型の反復子に対して特殊化されたクラステンプレート[Sub_match クラス](../standard-library/sub-match-class.md)を表します。

## <a name="see-also"></a>関連項目

[\<regex>](../standard-library/regex.md)\
[Regex_constants クラス](../standard-library/regex-constants-class.md)\
[Regex_error クラス](../standard-library/regex-error-class.md)\
[\<regex > 関数](../standard-library/regex-functions.md)\
[Regex_iterator クラス](../standard-library/regex-iterator-class.md)\
[\<regex > 演算子](../standard-library/regex-operators.md)\
[Regex_token_iterator クラス](../standard-library/regex-token-iterator-class.md)\
[regex_traits クラス](../standard-library/regex-traits-class.md)
