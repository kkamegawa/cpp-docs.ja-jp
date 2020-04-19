---
title: Platform::ArrayReference クラス
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ArrayReference::ArrayReference
helpviewer_keywords:
- Platform::ArrayReference Class
ms.assetid: 9ab3b15e-8a60-4600-8fcb-7d6c86284f4b
ms.openlocfilehash: f7e587902f1c99b294ed79255397aeffccee26b5
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72587928"
---
# <a name="platformarrayreference-class"></a>Platform::ArrayReference クラス

`ArrayReference` は、C スタイル配列に入力データを格納するときに、入力パラメーターの [Platform::Array^](../cppcx/platform-array-class.md) と置き換えることができる最適化の種類です。

## <a name="syntax"></a>構文

```cpp
class ArrayReference
```

### <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名|説明|
|----------|-----------------|
|[ArrayReference:: ArrayReference](#ctor)|`ArrayReference` クラスの新しいインスタンスを初期化します。|

### <a name="public-operators"></a>パブリック演算子

|名|説明|
|----------|-----------------|
|[ArrayReference::operator() 演算子](#operator-call)|この `ArrayReference` を `Platform::Array<T>^*`に変換します。|
|[ArrayReference::operator= 演算子](#operator-assign)|このインスタンスに別の `ArrayReference` の内容を割り当てます。|

## <a name="exceptions"></a>例外

### <a name="remarks"></a>Remarks

`ArrayReference` を使用して C スタイル配列にデータを格納する方法であれば、一度 `Platform::Array` 変数にコピーしたうえで改めて C スタイル配列にコピーするような余分な操作が不要になります。 `ArrayReference`を使用した場合には、コピー操作が 1 回のみとなります。 コード例については、「 [array と WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)」を参照してください。

### <a name="requirements"></a>［要件］

**サポートされている最低限のクライアント:** Windows 8

**サポートされる最小サーバー:** Windows Server 2012

**名前空間:** Platform

**ヘッダー:** vccorlib.h

## <a name="ctor"></a>ArrayReference:: ArrayReference コンストラクター

[Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md)クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
ArrayReference(TArg* ataArg, unsigned int sizeArg, bool needsInitArg = false);
ArrayReference(ArrayReference&& otherArg)
```

### <a name="parameters"></a>パラメーター

*dataArg*<br/>
配列データへのポインター。

*Siz氏 g*<br/>
ソース配列の要素数。

*otherArg*<br/>
新しいインスタンスを初期化するためにデータが移動される `ArrayReference` オブジェクト。

### <a name="remarks"></a>Remarks

## <a name="operator-assign"></a>ArrayReference:: operator = 演算子

移動セマンティクスを使用して、指定されたオブジェクトを現在の[Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md)オブジェクトに割り当てます。

### <a name="syntax"></a>構文

```cpp
ArrayReference& operator=(ArrayReference&& otherArg);
```

### <a name="parameters"></a>パラメーター

*otherArg*<br/>
現在の `ArrayReference` オブジェクトに移動されたオブジェクト。

### <a name="return-value"></a>戻り値

`ArrayReference` 型のオブジェクトへの参照。

### <a name="remarks"></a>Remarks

`Platform::ArrayReference` は、ref クラスではなく、標準 C++ クラス テンプレートです。

## <a name="operator-call"></a>ArrayReference:: operator () 演算子

現在の[platform:: ArrayReference](../cppcx/platform-arrayreference-class.md)オブジェクトを[Platform:: Array](../cppcx/platform-array-class.md)クラスに変換して返します。

### <a name="syntax"></a>構文

```cpp
Array<TArg>^ operator ();
```

### <a name="return-value"></a>戻り値

`Array<TArg>^` 型のオブジェクトへのハンドル。

### <a name="remarks"></a>Remarks

[Platform:: ArrayReference](../cppcx/platform-arrayreference-class.md)は標準C++クラステンプレートで、 [platform:: array](../cppcx/platform-array-class.md)は ref クラスです。

## <a name="see-also"></a>関連項目

[プラットフォーム名前空間](../cppcx/platform-namespace-c-cx.md)
