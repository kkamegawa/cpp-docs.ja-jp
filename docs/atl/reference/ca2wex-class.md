---
title: CA2WEX クラス
ms.date: 11/04/2016
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
ms.openlocfilehash: 927b9f5031bb6262c2f4a071b535802eb9e6990a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497961"
---
# <a name="ca2wex-class"></a>CA2WEX クラス

このクラスは、文字列変換マクロ CA2TEX、CA2CTEX、CT2WEX、CT2CWEX、および typedef CA2W によって使用されます。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <int t_nBufferLength = 128>
class CA2WEX
```

#### <a name="parameters"></a>パラメーター

*t_nBufferLength*<br/>
変換プロセスで使用されるバッファーのサイズ。 既定の長さは128バイトです。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CA2WEX::CA2WEX](#ca2wex)|コンストラクターです。|
|[CA2WEX:: ~ CA2WEX](#dtor)|デストラクターです。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CA2WEX:: operator LPWSTR](#operator_lpwstr)|変換演算子。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CA2WEX::m_psz](#m_psz)|ソース文字列を格納するデータメンバー。|
|[CA2WEX::m_szBuffer](#m_szbuffer)|変換された文字列を格納するために使用する静的バッファー。|

## <a name="remarks"></a>Remarks

追加機能が必要な場合を除き、コードで CA2TEX、CA2CTEX、CT2WEX、CT2CWEX、または CA2W を使用してください。

このクラスには、変換の結果を格納するために使用される固定サイズの静的バッファーが含まれています。 結果が大きすぎて静的バッファーに格納できない場合、クラスは**malloc**を使用してメモリを割り当て、オブジェクトがスコープ外に出るとメモリを解放します。 これにより、以前のバージョンの ATL で使用されていたテキスト変換マクロとは異なり、このクラスはループ内で安全に使用でき、スタックをオーバーフローすることはありません。

クラスがヒープにメモリを割り当てようとして失敗した場合は`AtlThrow` 、E_OUTOFMEMORY の引数を指定してを呼び出します。

既定では、ATL の変換クラスとマクロは、現在のスレッドの ANSI コードページを使用して変換を行います。 特定の変換に対してその動作をオーバーライドする場合は、クラスのコンストラクターの2番目のパラメーターとしてコードページを指定します。

次のマクロは、このクラスに基づいています。

- CA2TEX

- CA2CTEX

- CT2WEX

- CT2CWEX

次の typedef は、このクラスに基づいています。

- CA2W

これらのテキスト変換マクロの詳細については、「 [ATL および MFC の文字列変換マクロ](string-conversion-macros.md)」を参照してください。

## <a name="example"></a>例

これらの文字列変換マクロの使用例については、「 [ATL および MFC の文字列変換マクロ](string-conversion-macros.md)」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlconv. h

##  <a name="ca2wex"></a>CA2WEX::CA2WEX

コンストラクターです。

```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>パラメーター

*psz*<br/>
変換されるテキスト文字列。

*nCodePage*<br/>
変換を実行するために使用するコードページ。 詳細については、Windows SDK 関数[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)のコードページパラメーターの説明を参照してください。

### <a name="remarks"></a>Remarks

変換プロセスで使用されるバッファーを割り当てます。

##  <a name="dtor"></a>CA2WEX:: ~ CA2WEX

デストラクターです。

```
~CA2WEX() throw();
```

### <a name="remarks"></a>Remarks

割り当てられたバッファーを解放します。

##  <a name="m_psz"></a>  CA2WEX::m_psz

ソース文字列を格納するデータメンバー。

```
LPWSTR m_psz;
```

##  <a name="m_szbuffer"></a>CA2WEX::m_szBuffer

変換された文字列を格納するために使用する静的バッファー。

```
wchar_t m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpwstr"></a>  CA2WEX::operator LPWSTR

変換演算子。

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>戻り値

LPWSTR 型のテキスト文字列を返します。

## <a name="see-also"></a>関連項目

[CA2AEX クラス](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX クラス](../../atl/reference/ca2caex-class.md)<br/>
[CW2AEX クラス](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX クラス](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX クラス](../../atl/reference/cw2wex-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
