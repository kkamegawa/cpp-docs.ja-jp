---
title: '&lt;istream&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: fc512558969bc25d2b16afa2b93219e13d0b28ca
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874824"
---
# <a name="ltistreamgt-functions"></a>&lt;istream&gt; 関数

|||
|-|-|
|[スワップ](#istream_swap)|[ws](#ws)|

## <a name="istream_swap"></a>  swap

2 つのストリーム オブジェクトの要素を交換します。

```cpp
template <class Elem, class Tr>
void swap(
    basic_istream<Elem, Tr>& left,
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>
void swap(
    basic_iostream<Elem, Tr>& left,
    basic_iostream<Elem, Tr>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
ストリーム。

*右*\
ストリーム。

## <a name="ws"></a>  ws

ストリーム内の空白をスキップします。

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>パラメーター

*_Istr*\
ストリーム。

### <a name="return-value"></a>戻り値

ストリームです。

### <a name="remarks"></a>解説

マニピュレーターは、 [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **Elem**> > ( [getloc](../standard-library/ios-base-class.md#getloc)) `ch` すべての要素を抽出して破棄します。 **is**( **ctype**\< **Elem**>:: **space**, **ch**) が true です。

この関数は、要素の抽出中にファイルの終わりに達した場合 [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) を呼び出します。 *_Istr*が返されます。

### <a name="example"></a>例

[ の使用例については ](../standard-library/istream-operators.md#op_gt_gt)operator>>`ws` に関する記事をご覧ください。

## <a name="see-also"></a>参照

[\<istream>](../standard-library/istream.md)
