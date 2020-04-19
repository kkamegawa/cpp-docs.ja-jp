---
title: SafeIntException クラス
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeIntException Class
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
helpviewer_keywords:
- SafeIntException class
- SafeIntException, constructor
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
ms.openlocfilehash: 2998bbb83fd568d7ff627d6598c32fb5b17c1e40
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515567"
---
# <a name="safeintexception-class"></a>SafeIntException クラス

`SafeInt` クラスでは、数学演算を完了できない理由を特定するために `SafeIntException` を使用します。

> [!NOTE]
> このライブラリの最新バージョンは [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) にあります。

## <a name="syntax"></a>構文

```cpp
class SafeIntException;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

name                                                    | 説明
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | `SafeIntException` オブジェクトを作成します。

## <a name="remarks"></a>解説

[SafeInt クラス](../safeint/safeint-class.md)は、`SafeIntException` クラスを使用する唯一のクラスです。

## <a name="inheritance-hierarchy"></a>継承階層

`SafeIntException`

## <a name="requirements"></a>要件

**ヘッダー:** safeint.h

**名前空間:** msl::utilities

## <a name="safeintexception"></a>SafeIntException::SafeIntException

`SafeIntException` オブジェクトを作成します。

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>パラメーター

*code*<br/>
[in] 発生したエラーを説明する列挙データ値。

### <a name="remarks"></a>解説

*code* に使用できる値は、Safeint.h ファイルに定義されています。 参考までに、使用できる値を次に示します。

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
