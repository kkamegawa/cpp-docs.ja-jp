---
title: Platform::STAThreadAttribute クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
helpviewer_keywords:
- Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
ms.openlocfilehash: 05fb2879839c504f49f56e25ffe28329aa969c69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183379"
---
# <a name="platformstathreadattribute-class"></a>Platform::STAThreadAttribute クラス

アプリケーションのスレッド モデルがシングル スレッド アパートメント (STA) であることを示します。

## <a name="syntax"></a>構文

```
public ref class STAThreadAttribute sealed : Attribute
```

### <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[STAThreadAttribute コンストラクター 1](#ctor)|クラスの新しいインスタンスを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

STAThreadAttribute 属性が継承[platform::object Class](../cppcx/platform-object-class.md)します。 また STAThreadAttribute は次のメンバーもオーバーロードしたり、含んだりします。

|名前|説明|
|----------|-----------------|
|[STAThreadAttribute::Equals](#equals)|指定したオブジェクトが、現在のオブジェクトと等しいかどうかを判断します。|
|[STAThreadAttribute::GetHashCode](#gethashcode)|このインスタンスのハッシュ コードを返します。|
|[STAThreadAttribute::ToString](#tostring)|現在のオブジェクトを表す文字列を返します。|

## <a name="inheritance-hierarchy"></a>継承階層

`Platform`

### <a name="requirements"></a>必要条件

**ヘッダー:** collection.h

**名前空間:** プラットフォーム

## <a name="ctor"></a> STAThreadAttribute constructor

STAThreadAttribute クラスの新しいインスタンスを初期化します。

### <a name="syntax"></a>構文

```cpp
public:STAThreadAttribute();
```

## <a name="equals"></a> STAThreadAttribute::Equals

指定したオブジェクトが、現在のオブジェクトと等しいかどうかを判断します。

### <a name="syntax"></a>構文

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>パラメーター

*obj*<br/>
比較対象のオブジェクト。

### <a name="return-value"></a>戻り値

**true**オブジェクトが、それ以外の場合は**false**します。

## <a name="gethashcode"></a> STAThreadAttribute::GetHashCode

このインスタンスのハッシュ コードを返します。

### <a name="syntax"></a>構文

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>戻り値

対象のインスタンスのハッシュ コード。

## <a name="tostring"></a> STAThreadAttribute::ToString

現在のオブジェクトを表す文字列を返します。

### <a name="syntax"></a>構文

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>戻り値

現在のオブジェクトを表す文字列。

## <a name="see-also"></a>関連項目

[プラットフォーム Namespace](platform-namespace-c-cx.md)
