---
title: HStringReference クラス
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HStringReference class
- Microsoft::WRL::Wrappers::HStringReference::CopyTo method
- Microsoft::WRL::Wrappers::HStringReference::Get method
- Microsoft::WRL::Wrappers::HStringReference::HStringReference, constructor
- Microsoft::WRL::Wrappers::HStringReference::operator= operator
- Microsoft::WRL::Wrappers::HStringReference::operator== operator
- Microsoft::WRL::Wrappers::HStringReference::operator!= operator
- Microsoft::WRL::Wrappers::HStringReference::operator< operator
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
ms.openlocfilehash: b9d2e49d0a7e1321e2259c06e1313a90d55dc90e
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893250"
---
# <a name="hstringreference-class"></a>HStringReference クラス

既存の文字列から作成された HSTRING を表します。

## <a name="syntax"></a>構文

```cpp
class HStringReference;
```

## <a name="remarks"></a>Remarks

新しい HSTRING のバッキング バッファーの有効期間は、Windows ランタイムで管理されていません。 呼び出し元はソース文字列をスタック フレームに割り当てることで、ヒープ割り当てを回避し、メモリ リークのリスクを排除します。 また、呼び出し元はアタッチ済みの HSTRING の有効期間中にソース文字列が変更されないことを確認する必要があります。 詳細については、次を参照してください。 [WindowsCreateStringReference 関数](/windows/desktop/api/winstring/nf-winstring-windowscreatestringreference)します。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                                    | 説明
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference::HStringReference](#hstringreference) | `HStringReference` クラスの新しいインスタンスを初期化します。

### <a name="public-methods"></a>パブリック メソッド

メンバー                              | 説明
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | 現在のコピー`HStringReference`オブジェクトを HSTRING オブジェクトにします。
[HStringReference::Get](#get)       | 基になる HSTRING ハンドルの値を取得します。

### <a name="public-operators"></a>パブリック演算子

名前                                                  | 説明
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference::operator=](#operator-assign)       | 別の値を移動`HStringReference`現在オブジェクト`HStringReference`オブジェクト。
[HStringReference::operator==](#operator-equality)    | 2 つのパラメーターが等しいかどうかを示します。
[HStringReference::operator!=](#operator-inequality)  | 2 つのパラメーターが異なるかどうかを示します。
[HStringReference::operator&lt;](#operator-less-than) | 最初のパラメーターがかどうかが 2 番目のパラメーターを未満を示します。

## <a name="inheritance-hierarchy"></a>継承階層

`HStringReference`

## <a name="requirements"></a>必要条件

**ヘッダー:** corewrappers.h

**名前空間:** Microsoft::WRL::Wrappers

## <a name="copyto"></a>HStringReference::CopyTo

現在のコピー`HStringReference`オブジェクトを HSTRING オブジェクトにします。

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

## <a name="get"></a>HStringReference::Get

基になる HSTRING ハンドルの値を取得します。

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>戻り値

基になる HSTRING ハンドルの値。

## <a name="hstringreference"></a>HStringReference::HStringReference

`HStringReference` クラスの新しいインスタンスを初期化します。

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>パラメーター

*sizeDest*<br/>
変換先のサイズを指定するテンプレート パラメーター`HStringReference`バッファー。

*str*<br/>
ワイド文字の文字列への参照。

*len*<br/>
最大長、 *str*この操作で使用するパラメーターのバッファー。 場合、 *len*パラメーターが指定されていない全体*str*パラメーターを使用します。 場合*len*がより大きい*sizeDest*、 *len*に設定されている*sizeDest*-1。

*other*<br/>
もう 1 つ`HStringReference`オブジェクト。

### <a name="remarks"></a>Remarks

最初のコンス トラクターによって初期化新しい`HStringReference`オブジェクトをパラメーターとして、同じサイズ*str*します。

2 番目のコンス トラクターによって初期化新しい`HStringReference`オブジェクトをパラメーターでサイズ specifeid *len*します。

3 番目のコンス トラクターによって初期化、新しい`HStringReference`オブジェクトの値を*他*パラメーター、し、その後破棄、*他*パラメーター。

## <a name="operator-assign"></a>HStringReference::operator=

別の値を移動`HStringReference`現在オブジェクト`HStringReference`オブジェクト。

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>パラメーター

*other*<br/>
既存の `HStringReference` オブジェクト。

### <a name="remarks"></a>Remarks

既存の値*他*現在にオブジェクトがコピーされます`HStringReference`オブジェクト、し、*他*オブジェクトが破棄されます。

## <a name="operator-equality"></a>HStringReference::operator==

2 つのパラメーターが等しいかどうかを示します。

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
比較する最初のパラメーター。 *lhs*できます、`HStringReference`オブジェクトまたは HSTRING ハンドル。

*rhs*<br/>
比較する 2 番目のパラメーター。  *rhs*できます、`HStringReference`オブジェクトまたは HSTRING ハンドル。

### <a name="return-value"></a>戻り値

**true**場合、 *lhs*と*rhs*パラメーターは、それ以外の**false**します。

## <a name="operator-inequality"></a>HStringReference::operator!=

2 つのパラメーターが異なるかどうかを示します。

```cpp
inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
比較する最初のパラメーター。 *lhs*できます、`HStringReference`オブジェクトまたは HSTRING ハンドル。

*rhs*<br/>
比較する 2 番目のパラメーター。  *rhs*できます、`HStringReference`オブジェクトまたは HSTRING ハンドル。

### <a name="return-value"></a>戻り値

**true**場合、 *lhs*と*rhs*パラメーターが、それ以外の**false**します。

## <a name="operator-less-than"></a>HStringReference::operator&lt;

最初のパラメーターがかどうかが 2 番目のパラメーターを未満を示します。

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>パラメーター

*lhs*<br/>
比較する最初のパラメーター。 *lhs*への参照を指定できます、`HStringReference`します。

*rhs*<br/>
比較する 2 番目のパラメーター。  *rhs*への参照を指定できます、`HStringReference`します。

### <a name="return-value"></a>戻り値

**true**場合、 *lhs*パラメーターより小さい*rhs*パラメーター、それ以外の**false**します。
