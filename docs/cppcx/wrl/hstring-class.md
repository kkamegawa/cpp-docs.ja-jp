---
title: HString クラス
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
- corewrappers/Microsoft::WRL::Wrappers::HString::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator==
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
- corewrappers/Microsoft::WRL::Wrappers::HString::Release
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
- corewrappers/Microsoft::WRL::Wrappers::HString::~HString
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HString class
- Microsoft::WRL::Wrappers::HString::Attach method
- Microsoft::WRL::Wrappers::HString::CopyTo method
- Microsoft::WRL::Wrappers::HString::Detach method
- Microsoft::WRL::Wrappers::HString::Get method
- Microsoft::WRL::Wrappers::HString::GetAddressOf method
- Microsoft::WRL::Wrappers::HString::HString, constructor
- Microsoft::WRL::Wrappers::HString::IsValid method
- Microsoft::WRL::Wrappers::HString::MakeReference method
- Microsoft::WRL::Wrappers::HString::operator= operator
- Microsoft::WRL::Wrappers::HString::operator== operator
- Microsoft::WRL::Wrappers::HString::operator!= operator
- Microsoft::WRL::Wrappers::HString::operator< operator
- Microsoft::WRL::Wrappers::HString::Release method
- Microsoft::WRL::Wrappers::HString::Set method
- Microsoft::WRL::Wrappers::HString::~HString, destructor
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
ms.openlocfilehash: 71ebc02dc56b45e8790bfac7b7d4bac80d5f7729
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500498"
---
# <a name="hstring-class"></a>HString クラス

RAII パターンを使用して[Hstring](/windows/win32/WinRT/hstring)の有効期間を管理するためのヘルパークラス。

## <a name="syntax"></a>構文

```cpp
class HString;
```

## <a name="remarks"></a>Remarks

Windows ランタイムは、 [hstring](/windows/win32/WinRT/hstring)ハンドルを通じて文字列へのアクセスを提供します。 クラス`HString`には、hstring ハンドルの使用を簡略化するための便利な関数と演算子が用意されています。 このクラスは、RAII パターンを介して所有する HSTRING の有効期間を処理できます。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                | 説明
----------------------------------- | -----------------------------------------------------
[HString:: HString](#hstring)        | `HString` クラスの新しいインスタンスを初期化します。
[HString:: ~ HString](#tilde-hstring) | `HString`クラスの現在のインスタンスを破棄します。

### <a name="public-methods"></a>パブリック メソッド

名前                                     | 説明
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString:: Attach](#attach)               | 指定した`HString`オブジェクトを現在`HString`のオブジェクトに関連付けます。
[HString:: CopyTo](#copyto)               | 現在`HString`のオブジェクトを hstring オブジェクトにコピーします。
[HString::D etach](#detach)               | 指定した`HString`オブジェクトと基になる値との関連付けを解除します。
[HString:: Get](#get)                     | 基になる HSTRING ハンドルの値を取得します。
[HString:: GetAddressOf](#getaddressof)   | 基になる HSTRING ハンドルへのポインターを取得します。
[HString:: GetRawBuffer](#getrawbuffer)   | 基になる文字列データへのポインターを取得します。
[HString:: IsValid](#isvalid)             | 現在`HString`のオブジェクトが有効かどうかを示します。
[HString:: MakeReference](#makereference) | 指定した文字列パラメーターからオブジェクトを作成します。`HStringReference`
[HString:: Release](#release)             | 基になる文字列値を削除し、 `HString`現在のオブジェクトを空の値に初期化します。
[HString:: Set](#set)                     | 現在`HString`のオブジェクトの値を、指定したワイド文字列または`HString`パラメーターに設定します。

### <a name="public-operators"></a>パブリック演算子

名前                                         | 説明
-------------------------------------------- | ----------------------------------------------------------------------------
[HString:: operator =](#operator-assign)       | 別`HString`のオブジェクトの値を現在`HString`のオブジェクトに移動します。
[HString::operator==](#operator-equality)    | 2 つのパラメーターが等しいかどうかを示します。
[HString:: operator! =](#operator-inequality)  | 2 つのパラメーターが異なるかどうかを示します。
[HString:: operator&lt;](#operator-less-than) | 最初のパラメーターが2番目のパラメーターより小さいかどうかを示します。

## <a name="inheritance-hierarchy"></a>継承階層

`HString`

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers .h

**名前空間:** Microsoft:: WRL:: Wrapper

## <a name="tilde-hstring"></a>HString:: ~ HString

`HString`クラスの現在のインスタンスを破棄します。

```cpp
~HString() throw()
```

## <a name="attach"></a>HString:: Attach

指定した`HString`オブジェクトを現在`HString`のオブジェクトに関連付けます。

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>パラメーター

*hstr*<br/>
既存の `HString` オブジェクト。

## <a name="copyto"></a>HString:: CopyTo

現在`HString`のオブジェクトを hstring オブジェクトにコピーします。

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>パラメーター

*str*<br/>
コピーを受信する HSTRING です。

### <a name="remarks"></a>Remarks

このメソッドは、 [WindowsDuplicateString](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring)関数を呼び出します。

## <a name="detach"></a>HString::D etach

指定した`HString`オブジェクトと基になる値との関連付けを解除します。

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>戻り値

デタッチ操作`HString`が開始される前の基になる値。

## <a name="get"></a>HString:: Get

基になる HSTRING ハンドルの値を取得します。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>戻り値

基になる HSTRING ハンドルの値

## <a name="getaddressof"></a>HString:: GetAddressOf

基になる HSTRING ハンドルへのポインターを取得します。

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>戻り値

基になる HSTRING ハンドルへのポインター。

### <a name="remarks"></a>Remarks

この操作の後に、基になる HSTRING ハンドルの文字列値が破棄されます。

## <a name="getrawbuffer"></a>HString:: GetRawBuffer

基になる文字列データへのポインターを取得します。

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```
### <a name="parameters"></a>パラメーター

*長さ*データの長さを受け取る**int**変数へのポインター。

### <a name="return-value"></a>戻り値

基になる文字列データへの**const**ポインター。


## <a name="hstring"></a>HString:: HString

`HString` クラスの新しいインスタンスを初期化します。

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>パラメーター

*hstr*<br/>
HSTRING ハンドル。

*other*<br/>
既存の `HString` オブジェクト。

### <a name="remarks"></a>Remarks

最初のコンストラクターは、空`HString`の新しいオブジェクトを初期化します。

2番目のコンストラクターは`HString` 、新しいオブジェクトを既存*の他*のパラメーターの値に初期化し、*その他の*パラメーターを破棄します。

## <a name="isvalid"></a>HString:: IsValid

現在`HString`のオブジェクトが空であるかどうかを示します。

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>パラメーター

現在`HString`のオブジェクトが空でない場合は true、それ以外の場合は**false**。

## <a name="makereference"></a>HString:: MakeReference

指定した文字列パラメーターからオブジェクトを作成します。`HStringReference`

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>パラメーター

*sizeDest*<br/>
コピー先`HStringReference`のバッファーのサイズを指定するテンプレートパラメーター。

*str*<br/>
ワイド文字列への参照。

*len*<br/>
この操作で使用する*str*パラメーターバッファーの最大長。 *Len*パラメーターが指定されていない場合は、 *str*パラメーター全体が使用されます。

### <a name="return-value"></a>戻り値

指定した*str*パラメーターと同じ値を持つオブジェクト。`HStringReference`

## <a name="operator-assign"></a>HString:: operator = 演算子

別`HString`のオブジェクトの値を現在`HString`のオブジェクトに移動します。

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>パラメーター

*other*<br/>
既存の `HString` オブジェクト。

### <a name="remarks"></a>Remarks

既存のオブジェクトの値が現在`HString`のオブジェクトにコピーされ、*その他の*オブジェクトが破棄されます。

## <a name="operator-equality"></a>HString:: operator = = 演算子

2 つのパラメーターが等しいかどうかを示します。

```cpp
inline bool operator==(
               const HString& lhs,
               const HString& rhs) throw()

inline bool operator==(
                const HString& lhs,
                const HStringReference& rhs) throw()

inline bool operator==(
                const HStringReference& lhs,
                const HString& rhs) throw()

inline bool operator==(
                 const HSTRING& lhs,
                 const HString& rhs) throw()

inline bool operator==(
                 const HString& lhs,
                 const HSTRING& rhs) throw()
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
比較する最初のパラメーター。 *lhs*に`HString`は、オブジェクト`HStringReference`またはオブジェクト、または hstring ハンドルを指定できます。

*rhs*<br/>
比較する2番目のパラメーター。*rhs*に`HString`は、オブジェクト`HStringReference`またはオブジェクト、または hstring ハンドルを指定できます。

### <a name="return-value"></a>戻り値

*lhs*と*rhs*パラメーターが等しい場合は**true** 。それ以外の場合は**false**。

## <a name="operator-inequality"></a>HString:: operator! = 演算子

2 つのパラメーターが異なるかどうかを示します。

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
比較する最初のパラメーター。 *lhs*に`HString`は、オブジェクト`HStringReference`またはオブジェクト、または hstring ハンドルを指定できます。

*rhs*<br/>
比較する2番目のパラメーター。*rhs*に`HString`は、オブジェクト`HStringReference`またはオブジェクト、または hstring ハンドルを指定できます。

### <a name="return-value"></a>戻り値

*lhs*パラメーターと*rhs*パラメーターが等しくない場合は**true**を返します。それ以外の場合は**false**。

## <a name="operator-less-than"></a>Hstring:: operator&lt;演算子

最初のパラメーターが2番目のパラメーターより小さいかどうかを示します。

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
比較する最初のパラメーター。 *lhs*には、 `HString`への参照を指定できます。

*rhs*<br/>
比較する2番目のパラメーター。 *rhs*には、 `HString`への参照を指定できます。

### <a name="return-value"></a>戻り値

*lhs*パラメーターが*rhs*パラメーターより小さい場合は**true** 。それ以外の場合は**false**。

## <a name="release"></a>HString:: Release

基になる文字列値を削除し、 `HString`現在のオブジェクトを空の値に初期化します。

```cpp
void Release() throw()
```

## <a name="set"></a>HString:: Set

現在`HString`のオブジェクトの値を、指定したワイド文字列または`HString`パラメーターに設定します。

```cpp
HRESULT Set(
          const wchar_t* str) throw();
HRESULT Set(
          const wchar_t* str,
          unsigned int len
           ) throw();
HRESULT Set(
          const HSTRING& hstr
           ) throw();
```

### <a name="parameters"></a>パラメーター

*str*<br/>
ワイド文字列。

*len*<br/>
現在`HString`のオブジェクトに割り当てられている*str*パラメーターの最大長。

*hstr*<br/>
既存の `HString` オブジェクト。
