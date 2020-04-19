---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 47924c3d6bd1a2f45cdbac648f4f563c57ce8939
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459114"
---
# <a name="ltstringviewgt"></a>&lt;string_view&gt;

クラステンプレート`basic_string_view`と関連する型および演算子を定義します。 (コンパイラオプション[std: c++ 17](../build/reference/std-specify-language-standard-version.md)以降が必要)

## <a name="syntax"></a>構文

```cpp
#include <string_view>
```

## <a name="remarks"></a>Remarks

テンプレートの特殊化の string_view ファミリは、読み取り専用の例外セーフな非所有のハンドルを、0の位置にあるシーケンスの最初の要素を持つ文字列に似たオブジェクトの文字データに渡すための効率的な方法を提供します。 型`string_view` (の`basic_string_view<char>`typedef) の関数パラメーター `std::string`では、などの引数を受け取ることができます。このような引数に **\*** `string_view`は、の暗黙的な変換を行うために、、char、またはその他の文字列に似たナロー文字のクラスを使用できます。が定義されています。 同様に、、、 `wstring_view` `u16string_view`または`u32string_view`のパラメーターは、暗黙的な変換が定義されている任意の文字列型を受け入れることができます。 詳細については、「 [Basic_string_view クラス](../standard-library/basic-string-view-class.md)」を参照してください。

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|Char 型の要素を持つ`basic_string_view`クラステンプレートの特殊化。|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|Wchar_t 型の要素を持つ`basic_string_view`クラステンプレートの特殊化。|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|`basic_string_view` 型`char16_t`の要素を持つクラステンプレートの特殊化。|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|`basic_string_view` 型`char32_t`の要素を持つクラステンプレートの特殊化。|

### <a name="operators"></a>演算子

String_view \<> 演算子を使用する`string_view`と、オブジェクトを変換可能な文字列型のオブジェクトと比較できます。

|演算子|説明|
|-|-|
|[operator!=](../standard-library/string-view-operators.md#op_neq)|演算子の左側のオブジェクトが右側のオブジェクトと等しくないかどうかを調べます。|
|[operator==](../standard-library/string-view-operators.md#op_eq_eq)|演算子の左側のオブジェクトが右側のオブジェクトと等しいかどうかを調べます。|
|[operator<](../standard-library/string-view-operators.md#op_lt)|演算子の左側のオブジェクトが右側のオブジェクトより小さいかどうかをテストします。|
|[operator<=](../standard-library/string-view-operators.md#op_lt_eq)|演算子の左側のオブジェクトが右側のオブジェクト以下かどうかを調べます。|
|[operator<\<](../standard-library/string-view-operators.md#op_lt_lt)|を`string_view`出力ストリームに挿入するテンプレート関数。|
|[operator>](../standard-library/string-view-operators.md#op_gt)|演算子の左側のオブジェクトが右側のオブジェクトより大きいかどうかを調べます。|
|[operator>=](../standard-library/string-view-operators.md#op_gt_eq)|演算子の左側のオブジェクトが右側のオブジェクト以上であるかどうかを調べます。|

### <a name="literals"></a>リテラル

|演算子|説明|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|追加先の`wstring_view`文字列リテラルの`u32string_view`型に応じて`u16string_view`、、、、またはを構築します。 `string_view`|

### <a name="classes"></a>クラス

|クラス|説明|
|-|-|
|[basic_string_view クラス](../standard-library/basic-string-view-class.md)|任意の文字に似たオブジェクトのシーケンスに読み取り専用のビューを提供するクラステンプレート。|
|[hash](string-view-hash.md)|String_view のハッシュ値を生成する関数オブジェクト。|

## <a name="requirements"></a>必要条件

- **ヘッダー:** \<string_view >

- **名前空間:** std

- **コンパイラオプション:** std: c++ 17 (またはそれ以降)

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)
