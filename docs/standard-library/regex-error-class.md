---
title: regex_error クラス
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: 52b6bfd74a08200f7d924d2601b85718a941dd85
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451647"
---
# <a name="regexerror-class"></a>regex_error クラス

正しくない basic_regex オブジェクトを報告します。

## <a name="syntax"></a>構文

```cpp
class regex_error
: public std::runtime_error
```

## <a name="remarks"></a>Remarks

このクラスは、 `basic_regex` オブジェクトの構築時または使用時に発生したエラーを報告するためにスローされる例外オブジェクトを表します。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[regex_error](#regex_error)|オブジェクトを構築します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[code](#code)|エラー コードを返します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<regex>

**名前空間:** std

## <a name="example"></a>例

```cpp
// std__regex__regex_error.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex_error paren(std::regex_constants::error_paren);

    try
        {
        std::regex rx("(a");
        }
    catch (const std::regex_error& rerr)
        {
        std::cout << "regex error: "
            << (rerr.code() == paren.code() ? "unbalanced parentheses" : "")
            << std::endl;
        }
    catch (...)
        {
        std::cout << "unknown exception" << std::endl;
        }

    return (0);
    }
```

```Output
regex error: unbalanced parentheses
```

## <a name="code"></a>  regex_error::code

エラー コードを返します。

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、オブジェクトのコンストラクターに渡された値を返します。

## <a name="regex_error"></a>  regex_error::regex_error

オブジェクトを構築します。

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>パラメーター

*エラー*\
エラー コード。

### <a name="remarks"></a>Remarks

コンストラクターは、値*error*を保持するオブジェクトを構築します。

## <a name="see-also"></a>関連項目

[\<regex>](../standard-library/regex.md)\
[regex_constants クラス](../standard-library/regex-constants-class.md)\
[\<regex > 関数](../standard-library/regex-functions.md)\
[regex_iterator クラス](../standard-library/regex-iterator-class.md)\
[\<regex > 演算子](../standard-library/regex-operators.md)\
[regex_token_iterator クラス](../standard-library/regex-token-iterator-class.md)\
[regex_traits クラス](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
