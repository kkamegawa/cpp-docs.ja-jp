---
title: _bstr_t::_bstr_t
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::_bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
ms.openlocfilehash: 44a301b8b2a1c53636c27be6f59f61aa0dcd46b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385012"
---
# <a name="bstrtbstrt"></a>_bstr_t::_bstr_t

**Microsoft 固有の仕様**

`_bstr_t` オブジェクトを構築します。

## <a name="syntax"></a>構文

```
_bstr_t( ) throw( );
_bstr_t(
   const _bstr_t& s1
) throw( );
_bstr_t(
   const char* s2
);
_bstr_t(
   const wchar_t* s3
);
_bstr_t(
   const _variant_t& var
);
_bstr_t(
   BSTR bstr,
   bool fCopy
);
```

#### <a name="parameters"></a>パラメーター

*s1*<br/>
コピーされる `_bstr_t` オブジェクト。

*s2*<br/>
マルチバイト文字列。

*s3*<br/>
Unicode 文字列。

*var*<br/>
A [_variant_t](../cpp/variant-t-class.md)オブジェクト。

*bstr*<br/>
既存の `BSTR` オブジェクト。

*fCopy*<br/>
FALSE の場合、 *bstr*引数が呼び出すことによって、コピーを作成せず、新しいオブジェクトに接続されている`SysAllocString`します。

## <a name="remarks"></a>Remarks

`_bstr_t` のコンストラクターについて次の表で説明します。

|コンストラクター|説明|
|-----------------|-----------------|
|`_bstr_t( )`|既定値を構築します`_bstr_t`null 値をカプセル化するオブジェクト`BSTR`オブジェクト。|
|`_bstr_t( _bstr_t&`  `s1`  `)`|別のコピーとして `_bstr_t` オブジェクトを構築します。<br /><br /> これは、*浅い*コピーで、カプセル化されたの参照カウントをインクリメント`BSTR`オブジェクトを新規に作成する代わりにします。|
|`_bstr_t( char*`  `s2`  `)`|`_bstr_t` を呼び出して新しい `SysAllocString` オブジェクトを作成することで `BSTR` オブジェクトを構築し、そのオブジェクトをカプセル化します。<br /><br /> このコンストラクターは、マルチバイトから Unicode への変換を最初に実行します。|
|`_bstr_t( wchar_t*`  `s3`  `)`|`_bstr_t` を呼び出して新しい `SysAllocString` オブジェクトを作成することで `BSTR` オブジェクトを構築し、そのオブジェクトをカプセル化します。|
|`_bstr_t( _variant_t&`  `var`  `)`|最初に、カプセル化された VARIANT オブジェクトから `_bstr_t` オブジェクトを取得することによって、`_variant_t` オブジェクトから `BSTR` オブジェクトを構築します。|
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|(`_bstr_t` 文字列ではなく) 既存の `BSTR` から `wchar_t*` オブジェクトを構築します。 場合*fCopy*が false の場合、指定された`BSTR`の新しいコピーを作成せずに新しいオブジェクトにアタッチされます`SysAllocString`します。<br /><br /> このコンストラクターは、インターフェイス メソッドによって返される `BSTR` をカプセル化し、その所有権を得るために、タイプ ライブラリ ヘッダーのラッパー関数によって使用されます。|

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[_bstr_t クラス](../cpp/bstr-t-class.md)<br/>
[_variant_t クラス](../cpp/variant-t-class.md)