---
title: "regex_iterator クラス | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- regex_iterator
- std::regex_iterator
- regex/std::regex_iterator
- std::regex_iterator::operator==
- regex/std::regex_iterator::operator==
- std::regex_iterator::operator!=
- regex/std::regex_iterator::operator!=
- std::regex_iterator::operator*
- regex/std::regex_iterator::operator*
- std::regex_iterator::operator->
- regex/std::regex_iterator::operator->
- std::regex_iterator::operator++
- regex/std::regex_iterator::operator++
dev_langs:
- C++
helpviewer_keywords:
- regex_iterator class
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 248e9ba676b906af62f6804f4939e04158a8e2ef
ms.openlocfilehash: 8bfed3b74020bce20f18700d30573f01cdfd2adc
ms.lasthandoff: 02/24/2017

---
# <a name="regexiterator-class"></a>regex_iterator クラス
一致の反復子クラス。  
  
## <a name="syntax"></a>構文  
```
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator {  
public:  
   typedef basic_regex<Elem, RXtraits> regex_type;  
   typedef match_results<BidIt> value_type;  
   typedef std::forward_iterator_tag iterator_category;  
   typedef std::ptrdiff_t difference_type;  
   typedef const match_results<BidIt>* pointer;  
   typedef const match_results<BidIt>& reference;  

   regex_iterator();
   regex_iterator(
      BidIt first, BidIt last, const regex_type& re,  
      regex_constants::match_flag_type f = regex_constants::match_default);

   bool operator==(const regex_iterator& right);
   bool operator!=(const regex_iterator& right);
   const match_results<BidIt>& operator*();
   const match_results<BidIt> * operator->();
   regex_iterator& operator++();
   regex_iterator& operator++(int);

private:
   BidIt begin; // exposition only  
   BidIt end; // exposition only  
   regex_type *pregex;     // exposition only  
   regex_constants::match_flag_type flags; // exposition only  
   match_results<BidIt> match; // exposition only  
   };  
```  
  
### <a name="parameters"></a>パラメーター  
 `BidIt`  
 サブマッチ用の反復子の型。  
  
 `Elem`  
 一致させる要素の型。  
  
 `RXtraits`  
 要素の特徴 (traits) クラス。  
  
## <a name="remarks"></a>コメント  
 このテンプレート クラスは、定数前方反復子オブジェクトを表します。 反復子範囲 `match_results<BidIt>` で定義された文字シーケンスに正規表現オブジェクト `*pregex` を繰り返し適用することによって、 `[begin, end)`型のオブジェクトを抽出します。  
  
## <a name="examples"></a>例  
 正規表現の例については、以下の例をご覧ください。  
  
- [regex_match 関数](../standard-library/regex-functions.md#regex_match_function)  
  
- [regex_replace 関数](../standard-library/regex-functions.md#regex_replace_function)  
  
- [regex_search 関数](../standard-library/regex-functions.md#regex_search_function)  
  
- [swap 関数](../standard-library/regex-functions.md#swap_function)  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** \<regex>  
  
 **名前空間:** std  
  
##  <a name="a-nameregexiteratordifferencetypea--regexiteratordifferencetype"></a><a name="regex_iterator__difference_type"></a>  regex_iterator::difference_type  
 反復子の差の型です。  
  
```  
typedef std::ptrdiff_t difference_type;  
```  
  
### <a name="remarks"></a>コメント  
 この型は `std::ptrdiff_t` の同意語です。  
  
### <a name="example"></a>例  
  
```cpp  
// std__regex__regex_iterator_difference_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratoriteratorcategorya--regexiteratoriteratorcategory"></a><a name="regex_iterator__iterator_category"></a>  regex_iterator::iterator_category  
 反復子カテゴリの型。  
  
```  
typedef std::forward_iterator_tag iterator_category;  
```  
  
### <a name="remarks"></a>コメント  
 この型は `std::forward_iterator_tag` の同意語です。  
  
### <a name="example"></a>例  
  
```cpp  
// std__regex__regex_iterator_iterator_category.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratoroperatorneqa--regexiteratoroperator"></a><a name="regex_iterator__operator_neq"></a>  regex_iterator::operator!=  
 反復子の非等値を比較します。  
  
```  
bool operator!=(const regex_iterator& right);
```  
  
### <a name="parameters"></a>パラメーター  
 `right`  
 比較する反復子。  
  
### <a name="remarks"></a>コメント  
 このメンバー関数は、`!(*this == right)` を返します。  
  
### <a name="example"></a>例  
  
```cpp  
// std__regex__regex_iterator_operator_ne.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratoroperatorstara--regexiteratoroperator"></a><a name="regex_iterator__operator_star"></a>  regex_iterator::operator*  
 指定した一致にアクセスします。  
  
```  
const match_results<BidIt>& operator*();
```  
  
### <a name="remarks"></a>コメント  
 このメンバー関数は、格納されている値 `match` を返します。  
  
### <a name="example"></a>例  
  
```cpp  
// std__regex__regex_iterator_operator_star.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratoroperatoraddadda--regexiteratoroperator"></a><a name="regex_iterator__operator_add_add"></a>  regex_iterator::operator++  
 反復子をインクリメントします。  
  
```  
regex_iterator& operator++();
regex_iterator& operator++(int);
```  
  
### <a name="remarks"></a>コメント  
 現在の一致に文字が含まれていない場合は、最初の演算子が `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`を呼び出します。それ以外の場合は、現在の一致の後の最初の文字を指すように格納されている値 `begin` を増やしてから、 `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`を呼び出します。 どちらの場合も、検索に失敗したら、演算子がオブジェクトをシーケンス末尾の反復子に設定します。 演算子はそのオブジェクトを返します。  
  
 2 つ目の演算子は、オブジェクトのコピーを作成して、オブジェクトをインクリメントしてから、そのコピーを返します。  
  
### <a name="example"></a>例  
  
```cpp  
// std__regex__regex_iterator_operator_inc.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratoroperatoreqa--regexiteratoroperator"></a><a name="regex_iterator__operator_eq"></a>  regex_iterator::operator=  
 反復子が等しいかどうかを比較します。  
  
```  
bool operator==(const regex_iterator& right);
```  
  
### <a name="parameters"></a>パラメーター  
 `right`  
 比較する反復子。  
  
### <a name="remarks"></a>コメント  
 このメンバー関数は、 `*this` と `right` の両方がシーケンス末尾の反復子の場合、または両方がシーケンス末尾の反復子ではなく、 `begin == right.begin`、 `end == right.end`、 `pregex == right.pregex`、および `flags == right.flags` の場合に true を返します。 それ以外の場合は、false を返します。  
  
### <a name="example"></a>例  
  
```cpp  
// std__regex__regex_iterator_operator_as.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratoroperator-gta--regexiteratoroperator-gt"></a><a name="regex_iterator__operator-_gt_"></a>  regex_iterator::operator-&gt;  
 指定した一致にアクセスします。  
  
```  
const match_results<BidIt> * operator->();
```  
  
### <a name="remarks"></a>コメント  
 メンバー関数は、格納されている値 `match`のアドレスを返します。  
  
### <a name="example"></a>例  
  
```cpp  
// std__regex__regex_iterator_operator_arrow.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratorpointera--regexiteratorpointer"></a><a name="regex_iterator__pointer"></a>  regex_iterator::pointer  
 一致へのポインターの型です。  
  
```  
typedef match_results<BidIt> *pointer;  
```  
  
### <a name="remarks"></a>コメント  
 この型は `match_results<BidIt>*`のシノニムです。ここで `BidIt` はテンプレート パラメーターです。  
  
### <a name="example"></a>例  
  
```cpp  
// std__regex__regex_iterator_pointer.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratorreferencea--regexiteratorreference"></a><a name="regex_iterator__reference"></a>  regex_iterator::reference  
 一致を指す参照の型です。  
  
```  
typedef match_results<BidIt>& reference;  
```  
  
### <a name="remarks"></a>コメント  
 この型は `match_results<BidIt>&`のシノニムです。ここで `BidIt` はテンプレート パラメーターです。  
  
### <a name="example"></a>例  
  
```cpp  
// std__regex__regex_iterator_reference.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratorregexiteratora--regexiteratorregexiterator"></a><a name="regex_iterator__regex_iterator"></a>  regex_iterator::regex_iterator  
 反復子を構築します。  
  
```  
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,  
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```  
  
### <a name="parameters"></a>パラメーター  
 `first`  
 一致させるシーケンスの先頭。  
  
 `last`  
 一致させるシーケンスの末尾。  
  
 `re`  
 照合する正規表現。  
  
 `f`  
 一致のフラグ。  
  
### <a name="remarks"></a>コメント  
 1 つ目のコンストラクターは、シーケンス末尾の反復子を構築します。 2 番目のコンストラクターは、格納されている値 `begin` を `first`で、格納されている値 `end` を `last`で、格納されている値 `pregex` を `&re`で、格納されている値 `flags` を `f`でそれぞれ初期化します。 次に、 `regex_search(begin, end, match, *pregex, flags)`を呼び出します。 検索に失敗すると、コンストラクターがオブジェクトをシーケンス末尾の反復子に設定します。  
  
### <a name="example"></a>例  
  
```cpp  
// std__regex__regex_iterator_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratorregextypea--regexiteratorregextype"></a><a name="regex_iterator__regex_type"></a>  regex_iterator::regex_type  
 一致させる正規表現の型。  
  
```  
typedef basic_regex<Elem, RXtraits> regex_type;  
```  
  
### <a name="remarks"></a>コメント  
 typedef は、`basic_regex<Elem, RXtraits>` の同意語です。  
  
### <a name="example"></a>例  
  
```cpp  
// std__regex__regex_iterator_regex_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="a-nameregexiteratorvaluetypea--regexiteratorvaluetype"></a><a name="regex_iterator__value_type"></a>  regex_iterator::value_type  
 一致の型  
  
```  
typedef match_results<BidIt> value_type;  
```  
  
### <a name="remarks"></a>コメント  
 この型は `match_results<BidIt>`のシノニムです。ここで `BidIt` はテンプレート パラメーターです。  
  
### <a name="example"></a>例  
  
```cpp  
// std__regex__regex_iterator_value_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
## <a name="see-also"></a>関連項目  
[\<regex>](../standard-library/regex.md)  
[regex_constants クラス](../standard-library/regex-constants-class.md)  
[regex_error クラス](../standard-library/regex-error-class.md)  
[\<regex> 系関数](../standard-library/regex-functions.md)  
[regex_iterator クラス](../standard-library/regex-iterator-class.md)  
[\<regex> 系演算子](../standard-library/regex-operators.md)  
[regex_token_iterator クラス](../standard-library/regex-token-iterator-class.md)  
[regex_traits クラス](../standard-library/regex-traits-class.md)  
[\<regex> typedefs](../standard-library/regex-typedefs.md)  

  
