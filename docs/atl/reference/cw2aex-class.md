---
title: CW2AEX クラス
ms.date: 11/04/2016
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
ms.openlocfilehash: 4dda1cb9e54c44f7940475660bc629192b9ead61
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496263"
---
# <a name="cw2aex-class"></a>CW2AEX クラス

このクラスは、文字列変換マクロ CT2AEX、CW2TEX、CW2CTEX、CT2CAEX、および typedef CW2A によって使用されます。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>パラメーター

*t_nBufferLength*<br/>
変換プロセスで使用されるバッファーのサイズ。 既定の長さは128バイトです。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|コンストラクターです。|
|[CW2AEX:: ~ CW2AEX](#dtor)|デストラクターです。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CW2AEX:: operator LPSTR](#operator_lpstr)|変換演算子。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|ソース文字列を格納するデータメンバー。|
|[CW2AEX::m_szBuffer](#m_szbuffer)|変換された文字列を格納するために使用する静的バッファー。|

## <a name="remarks"></a>Remarks

追加機能が必要な場合を除き、コードで CT2AEX、CW2TEX、CW2CTEX、CT2CAEX、または CW2A を使用してください。

このクラスには、変換の結果を格納するために使用される固定サイズの静的バッファーが含まれています。 結果が大きすぎて静的バッファーに格納できない場合、クラスは**malloc**を使用してメモリを割り当て、オブジェクトがスコープ外に出るとメモリを解放します。 これにより、以前のバージョンの ATL で使用されていたテキスト変換マクロとは異なり、このクラスはループ内で安全に使用でき、スタックをオーバーフローすることはありません。

クラスがヒープにメモリを割り当てようとして失敗した場合は`AtlThrow` 、E_OUTOFMEMORY の引数を指定してを呼び出します。

既定では、ATL の変換クラスとマクロは、現在のスレッドの ANSI コードページを使用して変換を行います。 特定の変換に対してその動作をオーバーライドする場合は、クラスのコンストラクターの2番目のパラメーターとしてコードページを指定します。

次のマクロは、このクラスに基づいています。

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

次の typedef は、このクラスに基づいています。

- CW2A

これらのテキスト変換マクロの詳細については、「 [ATL および MFC の文字列変換マクロ](string-conversion-macros.md)」を参照してください。

## <a name="example"></a>例

これらの文字列変換マクロの使用例については、「 [ATL および MFC の文字列変換マクロ](string-conversion-macros.md)」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlconv. h

##  <a name="cw2aex"></a>CW2AEX::CW2AEX

コンストラクターです。

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>パラメーター

*psz*<br/>
変換されるテキスト文字列。

*nCodePage*<br/>
変換を実行するために使用するコードページ。 詳細については、Windows SDK 関数[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)のコードページパラメーターの説明を参照してください。

### <a name="remarks"></a>Remarks

変換プロセスで使用されるバッファーを割り当てます。

##  <a name="dtor"></a>CW2AEX:: ~ CW2AEX

デストラクターです。

```
~CW2AEX() throw();
```

### <a name="remarks"></a>Remarks

割り当てられたバッファーを解放します。

##  <a name="m_psz"></a>CW2AEX::m_psz

ソース文字列を格納するデータメンバー。

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>CW2AEX::m_szBuffer

変換された文字列を格納するために使用する静的バッファー。

```
char m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpstr"></a>CW2AEX:: operator LPSTR

変換演算子。

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>戻り値

テキスト文字列を型 LPSTR として返します。

## <a name="see-also"></a>関連項目

[CA2AEX クラス](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX クラス](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX クラス](../../atl/reference/ca2wex-class.md)<br/>
[CW2CWEX クラス](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX クラス](../../atl/reference/cw2wex-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
