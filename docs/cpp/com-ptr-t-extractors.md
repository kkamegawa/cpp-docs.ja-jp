---
title: _com_ptr_t 抽出
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
helpviewer_keywords:
- operator Interface& [C++]
- '* operator [C++], with specific objects'
- operator& [C++]
- operator* [C++]
- -> operator [C++], with specific objects
- '& operator [C++], with specific objects'
- operator Interface* [C++]
- operator * [C++]
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors [C++]
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
ms.openlocfilehash: bac1f9a139d2fb0092ef0869587ae8b54342fe82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399331"
---
# <a name="comptrt-extractors"></a>_com_ptr_t 抽出

**Microsoft 固有の仕様**

カプセル化された COM インターフェイス ポインターを抽出します。

## <a name="syntax"></a>構文

```
operator Interface*( ) const throw( );
operator Interface&( ) const;
Interface& operator*( ) const;
Interface* operator->( ) const;
Interface** operator&( ) throw( );
operator bool( ) const throw( );
```

## <a name="remarks"></a>Remarks

- **演算子インターフェイス**<strong>\*</strong>場合 NULL にはカプセル化されたインターフェイス ポインターを返します。

- **演算子インターフェイス &** をカプセル化されたインターフェイス ポインター、参照を取得し、ポインターが NULL の場合はエラーを発行します。

- **演算子**<strong>\*</strong>逆参照される場合に、実際のカプセル化されたインターフェイスと同様に機能するスマート ポインター オブジェクトを使用します。

- **演算子 ->** 逆参照される場合に、実際のカプセル化されたインターフェイスと同様に機能するスマート ポインター オブジェクトを使用します。

- **演算子 &** null の場合に置き換えて、任意のカプセル化されたインターフェイス ポインターを解放し、カプセル化されたポインターのアドレスを返します。 これにより、スマート ポインターによってアドレスが関数に渡される、*アウト*パラメーターが使用されるインターフェイス ポインターを返します。

- **operator bool**条件式で使用するスマート ポインター オブジェクトを使用します。 この演算子は、ポインターが NULL でない場合に TRUE を返します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_com_ptr_t クラス](../cpp/com-ptr-t-class.md)