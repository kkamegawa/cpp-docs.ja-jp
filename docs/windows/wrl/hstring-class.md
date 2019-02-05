---
title: HString クラス
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
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
ms.openlocfilehash: 9d660f507f50c00c8ccd6f19505f09285ede9e60
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893601"
---
# <a name="hstring-class"></a>HString クラス

有効期間を管理するためのヘルパー クラス、 [HSTRING](/windows/desktop/WinRT/hstring) RAII パターンを使用します。

## <a name="syntax"></a>構文

```cpp
class HString;
```

## <a name="remarks"></a>Remarks

Windows ランタイムを使用して文字列へのアクセスを提供する[HSTRING](/windows/desktop/WinRT/hstring)ハンドル。 `HString`クラスには、便利な関数および HSTRING ハンドルの使用を簡単に演算子が用意されています。 このクラスは、RAII パターンを所有している HSTRING の有効期間を処理できます。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                | 説明
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | `HString` クラスの新しいインスタンスを初期化します。
[HString:: ~ HString](#tilde-hstring) | 現在のインスタンスを破棄、`HString`クラス。

### <a name="public-methods"></a>パブリック メソッド

名前                                     | 説明
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::Attach](#attach)               | 指定した関連付けます`HString`オブジェクトと現在`HString`オブジェクト。
[HString::CopyTo](#copyto)               | 現在のコピー`HString`オブジェクトを HSTRING オブジェクトにします。
[HString::Detach](#detach)               | 指定された関連付けを解除`HString`その基になる値からオブジェクトです。
[HString::Get](#get)                     | 基になる HSTRING ハンドルの値を取得します。
[HString::GetAddressOf](#getaddressof)   | 基になる HSTRING ハンドルへのポインターを取得します。
[HString::IsValid](#isvalid)             | 示すかどうか、現在`HString`オブジェクトが無効です。
[HString::MakeReference](#makereference) | 作成、`HStringReference`オブジェクト指定した文字列パラメーターから。
[HString::Release](#release)             | 基になる文字列値を削除し、現在を初期化します。`HString`オブジェクトから空の値。
[HString::Set](#set)                     | 現在の値を設定`HString`ワイド文字の文字列を指定するオブジェクトまたは`HString`パラメーター。

### <a name="public-operators"></a>パブリック演算子

名前                                         | 説明
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::operator=](#operator-assign)       | 別の値を移動`HString`現在オブジェクト`HString`オブジェクト。
[HString::operator==](#operator-equality)    | 2 つのパラメーターが等しいかどうかを示します。
[HString::operator!=](#operator-inequality)  | 2 つのパラメーターが異なるかどうかを示します。
[HString::operator&lt;](#operator-less-than) | 最初のパラメーターがかどうかが 2 番目のパラメーターを未満を示します。

## <a name="inheritance-hierarchy"></a>継承階層

`HString`

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers

## <a name="tilde-hstring"></a>HString:: ~ HString

現在のインスタンスを破棄、`HString`クラス。

```cpp
~HString() throw()
```

## <a name="attach"></a>HString::Attach

指定した関連付けます`HString`オブジェクトと現在`HString`オブジェクト。

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>パラメーター

*hstr*<br/>
既存の `HString` オブジェクト。

## <a name="copyto"></a>HString::CopyTo

現在のコピー`HString`オブジェクトを HSTRING オブジェクトにします。

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>パラメーター

*str*<br/>
コピーを受信する HSTRING です。

### <a name="remarks"></a>Remarks

このメソッドは、 [WindowsDuplicateString](/windows/desktop/api/winstring/nf-winstring-windowsduplicatestring)関数。

## <a name="detach"></a>Hstring::detach

指定された関連付けを解除`HString`その基になる値からオブジェクトです。

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>戻り値

基になる`HString`デタッチ操作を開始する前に値。

## <a name="get"></a>HString::Get

基になる HSTRING ハンドルの値を取得します。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>戻り値

基になる HSTRING ハンドルの値

## <a name="getaddressof"></a>HString::GetAddressOf

基になる HSTRING ハンドルへのポインターを取得します。

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>戻り値

基になる HSTRING ハンドルへのポインター。

### <a name="remarks"></a>Remarks

この操作の後は、基になる HSTRING ハンドルの文字列値が破棄されます。

## <a name="hstring"></a>HString::HString

`HString` クラスの新しいインスタンスを初期化します。

```cpp
HString(HSTRING hstr = nullptr) throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>パラメーター

*hstr*<br/>
HSTRING ハンドルの場合。

*other*<br/>
既存の `HString` オブジェクト。

### <a name="remarks"></a>Remarks

最初のコンス トラクターによって初期化新しい`HString`オブジェクトが空です。

2 番目のコンス トラクターによって初期化、新しい`HString`オブジェクト、既存の値から*他*パラメーター、し、その後破棄、*他*パラメーター。

## <a name="isvalid"></a>HString::IsValid

示すかどうか、現在`HString`オブジェクトが空か。

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>パラメーター

**true**場合、現在`HString`オブジェクトがないと、空以外の場合、 **false**します。

## <a name="makereference"></a>HString::MakeReference

作成、`HStringReference`オブジェクト指定した文字列パラメーターから。

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
変換先のサイズを指定するテンプレート パラメーター`HStringReference`バッファー。

*str*<br/>
ワイド文字の文字列への参照。

*len*<br/>
最大長、 *str*この操作で使用するパラメーターのバッファー。 場合、 *len*パラメーターが指定されていない全体*str*パラメーターを使用します。

### <a name="return-value"></a>戻り値

`HStringReference`オブジェクトの値が指定したのと同じ*str*パラメーター。

## <a name="operator-assign"></a>Hstring::operator = 演算子

別の値を移動`HString`現在オブジェクト`HString`オブジェクト。

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>パラメーター

*other*<br/>
既存の `HString` オブジェクト。

### <a name="remarks"></a>Remarks

既存の値*他*現在にオブジェクトがコピーされます`HString`オブジェクト、し、*他*オブジェクトが破棄されます。

## <a name="operator-equality"></a>Hstring::operator = 演算子

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
比較する最初のパラメーター。 *lhs*できます、`HString`または`HStringReference`オブジェクト、または、HSTRING ハンドル。

*rhs*<br/>
比較する 2 番目のパラメーター。*rhs*できます、`HString`または`HStringReference`オブジェクト、または、HSTRING ハンドル。

### <a name="return-value"></a>戻り値

**true**場合、 *lhs*と*rhs*パラメーターは、それ以外の**false**します。

## <a name="operator-inequality"></a>Hstring::operator! = 演算子

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
比較する最初のパラメーター。 *lhs*できます、`HString`または`HStringReference`オブジェクト、または、HSTRING ハンドル。

*rhs*<br/>
比較する 2 番目のパラメーター。*rhs*できます、`HString`または`HStringReference`オブジェクト、または、HSTRING ハンドル。

### <a name="return-value"></a>戻り値

**true**場合、 *lhs*と*rhs*パラメーターが、それ以外の**false**します。

## <a name="operator-less-than"></a>Hstring::operator&lt;演算子

最初のパラメーターがかどうかが 2 番目のパラメーターを未満を示します。

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
比較する最初のパラメーター。 *lhs*への参照を指定できます、`HString`します。

*rhs*<br/>
比較する 2 番目のパラメーター。 *rhs*への参照を指定できます、`HString`します。

### <a name="return-value"></a>戻り値

**true**場合、 *lhs*パラメーターより小さい*rhs*パラメーター、それ以外の**false**します。

## <a name="release"></a>HString::Release

基になる文字列値を削除し、現在を初期化します。`HString`オブジェクトから空の値。

```cpp
void Release() throw()
```

## <a name="set"></a>Hstring::set

現在の値を設定`HString`ワイド文字の文字列を指定するオブジェクトまたは`HString`パラメーター。

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
ワイド文字の文字列。

*len*<br/>
最大長、 *str*パラメーターに現在割り当てられている`HString`オブジェクト。

*hstr*<br/>
既存の `HString` オブジェクト。
