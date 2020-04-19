---
title: ATL HTTP ユーティリティ関数
ms.date: 11/04/2016
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
ms.openlocfilehash: ca6dfdfb02f5ef629c6eb523744260f177a3309b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497974"
---
# <a name="atl-http-utility-functions"></a>ATL HTTP ユーティリティ関数

これらの関数は、Url の操作をサポートします。

|||
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes は、安全でない文字やスペースをエスケープシーケンスに変換するなど、URL を指定します。|
|[AtlCombineUrl](#atlcombineurl)|ベース URL と相対 URL を結合して、1つの正規の URL にします。|
|[AtlEscapeUrl](#atlescapeurl)|安全でないすべての文字をエスケープシーケンスに変換します。|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|特定のインターネットプロトコルまたはスキームに関連付けられている既定のポート番号を取得します。|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|文字が URL で安全に使用できるかどうかを判断します。|
|[AtlUnescapeUrl](#atlunescapeurl)|エスケープされた文字を元の値に変換します。|
|[RGBToHtml](#rgbtohtml)|[COLORREF](/windows/win32/gdi/colorref)値をその色の値に対応する HTML テキストに変換します。|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|システム時刻を HTTP ヘッダーで使用できる形式の文字列に変換します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlutil. h

## <a name="atlcanonicalizeurl"></a>AtlCanonicalizeUrl

URL を標準形式に変換します。安全でない文字や空白をエスケープ シーケンスに変換する処理などが含まれます。

```cpp
inline BOOL AtlCanonicalizeUrl(
   LPCTSTR szUrl,
   LPTSTR szCanonicalized,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>パラメーター

*szUrl*<br/>
正規化される URL。

*szCanonicalized*<br/>
正規化された URL を受信するために、呼び出し元が割り当てたバッファー。

*pdwMaxLength*<br/>
*Szcanonicalized*された長さの文字数を格納している変数へのポインター。 関数が成功した場合、変数はバッファーに書き込まれた文字数 (終端の null 文字を含む) を受け取ります。 関数が失敗した場合、変数は、終端の null 文字の領域を含む、バッファーの必要な長さをバイト単位で受け取ります。

*dwFlags*<br/>
この関数の動作を制御する ATL_URL フラグ。

- ATL_URL_BROWSER_MODE は、"#" または "?" の後の文字をエンコードまたはデコードしません。また、"?" の後の末尾の空白は削除されません。 この値が指定されていない場合は、URL 全体がエンコードされ、末尾の空白が削除されます。

- ATL_URL_DECODE は、URL が解析される前に、すべての% XX シーケンスをエスケープシーケンスを含む文字に変換します。

- ATL_URL_ENCODE_PERCENT は、検出されたパーセント記号をエンコードします。 既定では、パーセント記号はエンコードされません。

- ATL_URL_ENCODE_SPACES_ONLY は、スペースのみをエンコードします。

- ATL_URL_ESCAPE は、すべてのエスケープシーケンス (% XX) を対応する文字に変換します。

- ATL_URL_NO_ENCODE は、安全でない文字をエスケープシーケンスに変換しません。

- ATL_URL_NO_META は、URL からメタシーケンス ("." や ".." など) を削除しません。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

現在のバージョンの[InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw)のように動作しますが、WinInet や Internet Explorer をインストールする必要はありません。

## <a name="atlcombineurl"></a> AtlCombineUrl

ベース URL と相対 URL を結合して、1 つの標準形式の URL にします。

```cpp
inline BOOL AtlCombineUrl(
   LPCTSTR szBaseUrl,
   LPCTSTR szRelativeUrl,
   LPTSTR szBuffer,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>パラメーター

*szBaseUrl*<br/>
ベース URL。

*szRelativeUrl*<br/>
ベース URL に対して相対的な URL。

*szBuffer*<br/>
正規化された URL を受信するために、呼び出し元が割り当てたバッファー。

*pdwMaxLength*<br/>
*Szbuffer*の長さを文字数で格納している変数へのポインター。 関数が成功した場合、変数はバッファーに書き込まれた文字数 (終端の null 文字を含む) を受け取ります。 関数が失敗した場合、変数は、終端の null 文字の領域を含む、バッファーの必要な長さをバイト単位で受け取ります。

*dwFlags*<br/>
この関数の動作を制御するフラグ。 「 [AtlCanonicalizeUrl](#atlcanonicalizeurl)」を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

は、現在のバージョンの[Internet連結 Eurl](/windows/win32/api/wininet/nf-wininet-internetcombineurlw)のように動作しますが、WinInet や Internet Explorer をインストールする必要はありません。

## <a name="atlescapeurl"></a> AtlEscapeUrl

すべての安全でない文字をエスケープ シーケンスに変換します。

```cpp
inline BOOL AtlEscapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();

inline BOOL AtlEscapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>パラメーター

*lpszStringIn*<br/>
変換する URL。

*lpszStringOut*<br/>
変換後の URL の書き込み先となる、呼び出し元が割り当てたバッファー。

*pdwStrLen*<br/>
DWORD 変数へのポインター。 関数が成功した場合、 *pdwStrLen*は、バッファーに書き込まれた文字数 (終端の null 文字を含む) を受け取ります。 関数が失敗した場合、変数は、終端の null 文字の領域を含む、バッファーの必要な長さをバイト単位で受け取ります。 このメソッドのワイド文字バージョンを使用する場合、 *pdwStrLen*は、バイト数ではなく、必要な文字数を受け取ります。

*dwMaxLength*<br/>
バッファー *Lpszstringout*のサイズ。

*dwFlags*<br/>
この関数の動作を制御する ATL_URL フラグ。 使用可能な値については、 [ATLCanonicalizeUrl](#atlcanonicalizeurl)を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

## <a name="atlgetdefaulturlport"></a> AtlGetDefaultUrlPort

特定のインターネット プロトコルまたはスキームに関連付けられた、既定のポート番号を取得します。

```
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();
```

### <a name="parameters"></a>パラメーター

*m_nScheme*<br/>
ポート番号を取得するスキームを識別する[ATL_URL_SCHEME](atl-url-scheme-enum.md)値。

### <a name="return-value"></a>戻り値

指定したスキームに関連付けられている[ATL_URL_PORT](atl-typedefs.md#atl_url_port) 、またはスキームが認識されない場合は ATL_URL_INVALID_PORT_NUMBER。

## <a name="atlisunsafeurlchar"></a> AtlIsUnsafeUrlChar

URL で使用しても安全な文字かどうかを判断します。

```
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();
```

### <a name="parameters"></a>パラメーター

*chIn*<br/>
安全性をテストする文字。

### <a name="return-value"></a>戻り値

入力文字が安全でない場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

Url で使用しない文字は、この関数を使用してテストし、 [AtlCanonicalizeUrl](#atlcanonicalizeurl)を使用して変換することができます。

## <a name="atlunescapeurl"></a> AtlUnescapeUrl

エスケープされた文字を元の値に変換します。

```cpp
inline BOOL AtlUnescapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();

inline BOOL AtlUnescapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();
```

### <a name="parameters"></a>パラメーター

*lpszStringIn*<br/>
変換する URL。

*lpszStringOut*<br/>
変換後の URL の書き込み先となる、呼び出し元が割り当てたバッファー。

*pdwStrLen*<br/>
DWORD 変数へのポインター。 関数が成功した場合、変数はバッファーに書き込まれた文字数 (終端の null 文字を含む) を受け取ります。 関数が失敗した場合、変数は、終端の null 文字の領域を含む、バッファーの必要な長さをバイト単位で受け取ります。

*dwMaxLength*<br/>
バッファー *Lpszstringout*のサイズ。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

[AtlEscapeUrl](#atlescapeurl)によって適用された変換処理を反転します。

## <a name="rgbtohtml"></a> RGBToHtml

[COLORREF](/windows/win32/gdi/colorref)値をその色の値に対応する HTML テキストに変換します。

```cpp
bool inline RGBToHtml(
   COLORREF color,
   LPTSTR pbOut,
   long nBuffer);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
RGB カラー値。

*pbOut*<br/>
HTML カラー値のテキストを受信するために、呼び出し元が割り当てたバッファー。 バッファーには、null 終端文字のスペースを含む8文字以上の領域が必要です。

*nBuffer*<br/>
バッファーのサイズ (null 終端文字のスペースを含む)。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

HTML カラー値は、カラーの赤、緑、および青の各成分に対して2桁を使用する、シャープ記号と6桁の16進数の値 (たとえば、#FFFFFF が白) です。

## <a name="systemtimetohttpdate"></a> SystemTimeToHttpDate

システム時刻を HTTP ヘッダーで使用できる形式の文字列に変換します。

```cpp
inline void SystemTimeToHttpDate(
   const SYSTEMTIME& st,
   CStringA& strTime);
```

### <a name="parameters"></a>パラメーター

*&*<br/>
HTTP 書式指定文字列として取得されるシステム時刻。

*strTime*<br/>
Rfc 2616 ([https://www.ietf.org/rfc/rfc2616.txt](https://www.ietf.org/rfc/rfc2616.txt)) および rfc 1123 ([https://www.ietf.org/rfc/rfc1123.txt](https://www.ietf.org/rfc/rfc1123.txt)) で定義されている HTTP 日付時刻を受け取る文字列変数への参照。

## <a name="see-also"></a>関連項目

[概念](../active-template-library-atl-concepts.md)<br/>
[ATL COM デスクトップ コンポーネント](../atl-com-desktop-components.md)<br/>
[InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw)
