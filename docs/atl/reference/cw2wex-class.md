---
title: CW2WEX クラス
ms.date: 11/04/2016
f1_keywords:
- CW2WEX
- ATLCONV/ATL::CW2WEX
- ATLCONV/ATL::CW2WEX::CW2WEX
- ATLCONV/ATL::CW2WEX::m_psz
- ATLCONV/ATL::CW2WEX::m_szBuffer
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
ms.openlocfilehash: d6d68f4f5c0f3532c39fee3f513e7b3102ec075d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277137"
---
# <a name="cw2wex-class"></a>CW2WEX クラス

このクラスは、文字列変換マクロ CW2TEX と CT2WEX、typedef CW2W によって使用されます。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <int t_nBufferLength = 128>
class CW2WEX
```

#### <a name="parameters"></a>パラメーター

*t_nBufferLength*<br/>
変換プロセスで使用されるバッファーのサイズ。 既定の長さは 128 バイトです。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CW2WEX::CW2WEX](#cw2wex)|コンストラクターです。|
|[CW2WEX:: ~ CW2WEX](#dtor)|デストラクターです。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CW2WEX::operator LPWSTR](#operator_lpwstr)|変換演算子。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CW2WEX::m_psz](#m_psz)|ソース文字列が格納されるデータ メンバー。|
|[CW2WEX::m_szBuffer](#m_szbuffer)|変換後の文字列の格納に使用される静的バッファー。|

## <a name="remarks"></a>Remarks

追加の機能が必要な場合を除き、CW2TEX、CT2WEX、または CW2W をコードで使用します。

このクラスには、固定サイズの静的バッファー変換の結果を格納するために使用が含まれています。 クラスでは、メモリを使用して割り当てます、結果が大きすぎて静的バッファーに収まるように場合、 **malloc**オブジェクトがスコープ外になるときに、メモリを解放します。 これにより、テキストとは異なり、ATL のこのクラスを安全にループ内で使用して、スタックがオーバーフローするしませんの以前のバージョンで使用できる変換マクロ。

クラスは、失敗をヒープにメモリの割り当てを試みると、それが呼び出す`AtlThrow`E_OUTOFMEMORY の引数を指定しています。

既定では、ATL 変換クラスとマクロは、変換の現在のスレッドの ANSI コード ページを使用します。

次のマクロは、このクラスに基づいています。

- CW2TEX

- CT2WEX

次の typedef は、このクラスに基づいています。

- CW2W

これらのテキスト変換マクロの詳細については、次を参照してください。 [ATL と MFC 文字列変換マクロ](string-conversion-macros.md)します。

## <a name="example"></a>例

参照してください[ATL と MFC 文字列変換マクロ](string-conversion-macros.md)のこれらの文字列変換マクロの使用例についてはします。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlconv.h

##  <a name="cw2wex"></a>  CW2WEX::CW2WEX

コンストラクターです。

```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```

### <a name="parameters"></a>パラメーター

*psz*<br/>
変換するテキスト文字列。

*nCodePage*<br/>
コード ページです。 このクラスでは使用されません。

### <a name="remarks"></a>Remarks

翻訳のために必要なバッファーを作成します。

##  <a name="dtor"></a>  CW2WEX:: ~ CW2WEX

デストラクター.

```
~CW2WEX() throw();
```

### <a name="remarks"></a>Remarks

割り当てられたバッファーを解放します。

##  <a name="m_psz"></a>  CW2WEX::m_psz

ソース文字列が格納されるデータ メンバー。

```
LPWSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CW2WEX::m_szBuffer

変換後の文字列の格納に使用される静的バッファー。

```
wchar_t m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpwstr"></a>  CW2WEX::operator LPWSTR

キャスト演算子です。

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>戻り値

LPWSTR を入力すると、テキスト文字列を返します。

## <a name="see-also"></a>関連項目

[CA2AEX クラス](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX クラス](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX クラス](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX クラス](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX クラス](../../atl/reference/cw2cwex-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
