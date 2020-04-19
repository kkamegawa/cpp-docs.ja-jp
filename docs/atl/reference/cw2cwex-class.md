---
title: CW2CWEX クラス
ms.date: 11/04/2016
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
ms.openlocfilehash: d1f960f8ec94b8e573490d4e708d4240b894b5ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277153"
---
# <a name="cw2cwex-class"></a>CW2CWEX クラス

このクラスは、文字列変換マクロ CW2CTEX と CT2CWEX、typedef CW2W によって使用されます。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<int t_nBufferLength = 128>
class CW2CWEX
```

#### <a name="parameters"></a>パラメーター

*t_nBufferLength*<br/>
変換プロセスで使用されるバッファーのサイズ。 既定の長さは 128 バイトです。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CW2CWEX::CW2CWEX](#cw2cwex)|コンストラクターです。|
|[CW2CWEX:: ~ CW2CWEX](#dtor)|デストラクターです。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CW2CWEX::operator LPCWSTR](#operator_lpcwstr)|変換演算子。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CW2CWEX::m_psz](#m_psz)|ソース文字列が格納されるデータ メンバー。|

## <a name="remarks"></a>Remarks

追加の機能が必要な場合を除き、CW2CTEX、CT2CWEX、または CW2W をコードで使用します。

このクラスは、安全にループ内で使用し、スタック オーバーフローが発生しません。 既定では、ATL 変換クラスとマクロは、変換の現在のスレッドの ANSI コード ページを使用します。

次のマクロは、このクラスに基づいています。

- CW2CTEX

- CT2CWEX

次の typedef は、このクラスに基づいています。

- CW2W

これらのテキスト変換マクロの詳細については、次を参照してください。 [ATL と MFC 文字列変換マクロ](string-conversion-macros.md)します。

## <a name="example"></a>例

参照してください[ATL と MFC 文字列変換マクロ](string-conversion-macros.md)のこれらの文字列変換マクロの使用例についてはします。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlconv.h

##  <a name="cw2cwex"></a>  CW2CWEX::CW2CWEX

コンストラクターです。

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>パラメーター

*psz*<br/>
変換するテキスト文字列。

*nCodePage*<br/>
コード ページです。 このクラスでは使用されません。

### <a name="remarks"></a>Remarks

変換プロセスで使用されるバッファーを割り当てます。

##  <a name="dtor"></a>  CW2CWEX:: ~ CW2CWEX

デストラクターです。

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>Remarks

割り当てられたバッファーを解放します。

##  <a name="m_psz"></a>  CW2CWEX::m_psz

ソース文字列が格納されるデータ メンバー。

```
LPCWSTR m_psz;
```

##  <a name="operator_lpcwstr"></a>  CW2CWEX::operator LPCWSTR

変換演算子。

```
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>戻り値

LPCWSTR を入力すると、テキスト文字列を返します。

## <a name="see-also"></a>関連項目

[CA2AEX クラス](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX クラス](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX クラス](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX クラス](../../atl/reference/cw2aex-class.md)<br/>
[CW2WEX クラス](../../atl/reference/cw2wex-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
