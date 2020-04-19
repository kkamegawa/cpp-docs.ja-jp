---
title: CComBSTR クラス
ms.date: 11/04/2016
f1_keywords:
- CComBSTR
- ATLBASE/ATL::CComBSTR
- ATLBASE/ATL::CComBSTR::CComBSTR
- ATLBASE/ATL::CComBSTR::Append
- ATLBASE/ATL::CComBSTR::AppendBSTR
- ATLBASE/ATL::CComBSTR::AppendBytes
- ATLBASE/ATL::CComBSTR::ArrayToBSTR
- ATLBASE/ATL::CComBSTR::AssignBSTR
- ATLBASE/ATL::CComBSTR::Attach
- ATLBASE/ATL::CComBSTR::BSTRToArray
- ATLBASE/ATL::CComBSTR::ByteLength
- ATLBASE/ATL::CComBSTR::Copy
- ATLBASE/ATL::CComBSTR::CopyTo
- ATLBASE/ATL::CComBSTR::Detach
- ATLBASE/ATL::CComBSTR::Empty
- ATLBASE/ATL::CComBSTR::Length
- ATLBASE/ATL::CComBSTR::LoadString
- ATLBASE/ATL::CComBSTR::ReadFromStream
- ATLBASE/ATL::CComBSTR::ToLower
- ATLBASE/ATL::CComBSTR::ToUpper
- ATLBASE/ATL::CComBSTR::WriteToStream
- ATLBASE/ATL::CComBSTR::m_str
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
ms.openlocfilehash: dd45c2ff9b43148e0fe27ebd410a2390a4d12ce2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497554"
---
# <a name="ccombstr-class"></a>CComBSTR クラス

このクラスは、 [BSTR](/previous-versions/windows/desktop/automat/bstr)のラッパーです。

## <a name="syntax"></a>構文

```
class CComBSTR
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComBSTR:: CComBSTR](#ccombstr)|コンストラクターです。|
|[CComBSTR::~CComBSTR](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComBSTR:: Append](#append)|に`m_str`文字列を追加します。|
|[CComBSTR::AppendBSTR](#appendbstr)|BSTR をに`m_str`追加します。|
|[CComBSTR:: AppendBytes](#appendbytes)|に`m_str`指定されたバイト数を追加します。|
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Safearray 内の各要素の最初の文字から BSTR を作成し、それを`CComBSTR`オブジェクトにアタッチします。|
|[CComBSTR::AssignBSTR](#assignbstr)|BSTR をに`m_str`割り当てます。|
|[CComBSTR:: Attach](#attach)|BSTR を`CComBSTR`オブジェクトにアタッチします。|
|[CComBSTR:: BSTRToArray](#bstrtoarray)|0から始まる1次元の safearray を作成します。配列の各要素は、 `CComBSTR`オブジェクトの文字です。|
|[CComBSTR::ByteLength](#bytelength)|の`m_str`長さをバイト単位で返します。|
|[CComBSTR:: Copy](#copy)|の`m_str`コピーを返します。|
|[CComBSTR::CopyTo](#copyto)|**[Out]** パラメーター `m_str`を使用してのコピーを返します。|
|[CComBSTR::D します。](#detach)|オブジェクトからデタッチ`m_str`します。 `CComBSTR`|
|[CComBSTR:: Empty](#empty)|解放`m_str`します。|
|[CComBSTR::Length](#length)|の`m_str`長さを返します。|
|[CComBSTR::LoadString](#loadstring)|文字列リソースを読み込みます。|
|[CComBSTR::ReadFromStream](#readfromstream)|ストリームから BSTR オブジェクトを読み込みます。|
|[CComBSTR:: ToLower](#tolower)|文字列を小文字に変換します。|
|[CComBSTR:: ToUpper](#toupper)|文字列を大文字に変換します。|
|[CComBSTR:: WriteToStream](#writetostream)|ストリーム`m_str`に保存します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CComBSTR:: operator BSTR](#operator_bstr)|オブジェクトを`CComBSTR` BSTR にキャストします。|
|[CComBSTR:: operator!](#operator_not)|が NULL かどうか`m_str`に応じて、TRUE または FALSE を返します。|
|[CComBSTR:: operator! =](#operator_neq)|と`CComBSTR`文字列を比較します。|
|[CComBSTR:: operator &](#operator_amp)|の`m_str`アドレスを返します。|
|[CComBSTR:: operator + =](#operator_add_eq)|オブジェクトに`CComBSTR`を追加します。|
|[CComBSTR:: operator <](#operator_lt)|と`CComBSTR`文字列を比較します。|
|[CComBSTR:: operator =](#operator_eq)|に`m_str`値を割り当てます。|
|[CComBSTR:: operator = =](#operator_eq_eq)|と`CComBSTR`文字列を比較します。|
|[CComBSTR:: operator >](#operator_gt)|と`CComBSTR`文字列を比較します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CComBSTR:: m_str](#m_str)|`CComBSTR`オブジェクトに関連付けられている BSTR を格納します。|

## <a name="remarks"></a>Remarks

`CComBSTR`クラスは bstr のラッパーであり、これはプレフィックスが付けられた文字列です。 長さは、文字列のデータの前のメモリ位置に整数として格納されます。

[BSTR](/previous-versions/windows/desktop/automat/bstr)は、最後にカウントされた文字の後に null で終了しますが、文字列内に埋め込まれた null 文字を含めることもできます。 文字列の長さは、最初の null 文字ではなく、文字数によって決まります。

> [!NOTE]
>  クラス`CComBSTR`には、引数として ANSI 文字列または Unicode 文字列を受け取る多数のメンバー (コンストラクター、代入演算子、および比較演算子) が用意されています。 一時的な Unicode 文字列は多くの場合、内部的に作成されるため、これらの関数の ANSI バージョンは、Unicode 対応の関数よりも効率が悪くなります。 効率を上げるには、可能な限り Unicode バージョンを使用します。

> [!NOTE]
>  Visual Studio .net で実装される検索動作が向上したため、 `bstr = L"String2" + bstr;`以前のリリースでコンパイルされたなどのコードは、と`bstr = CStringW(L"String2") + bstr`して実装する必要があります。

を使用`CComBSTR`する場合の注意事項の一覧については、「 [CComBSTR を使用](../../atl/programming-with-ccombstr-atl.md)したプログラミング」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase. h

##  <a name="append"></a>  CComBSTR::Append

*Lpsz*または*BSTRSRC*の BSTR メンバーを[m_str](#m_str)に追加します。

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>パラメーター

*bstrSrc*<br/>
から追加`CComBSTR`するオブジェクト。

*ch*<br/>
から追加する文字。

*lpsz*<br/>
から追加する0で終わる文字列。 LPCOLESTR オーバーロードまたは LPCSTR バージョンを使用して ANSI 文字列を使用して、Unicode 文字列を渡すことができます。

*nLen*<br/>
から*Lpsz*から追加する文字数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、または標準の HRESULT エラー値。

### <a name="remarks"></a>Remarks

ANSI 文字列は、追加される前に Unicode に変換されます。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

##  <a name="appendbstr"></a>  CComBSTR::AppendBSTR

指定した BSTR を[m_str](#m_str)に追加します。

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
から追加する BSTR。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、または標準の HRESULT エラー値。

### <a name="remarks"></a>Remarks

通常のワイド文字列をこのメソッドに渡さないでください。 コンパイラはエラーをキャッチできず、実行時エラーが発生します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

##  <a name="appendbytes"></a>CComBSTR:: AppendBytes

変換せずに、指定したバイト数を[m_str](#m_str)に追加します。

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>パラメーター

*lpsz*<br/>
から追加するバイト配列へのポインター。

*p*<br/>
から追加するバイト数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、または標準の HRESULT エラー値。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

##  <a name="arraytobstr"></a>  CComBSTR::ArrayToBSTR

`CComBSTR`オブジェクトに保持されている既存の文字列を解放し、safearray 内の各要素の最初の文字から BSTR を作成し`CComBSTR` 、オブジェクトにアタッチします。

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>パラメーター

*.Psrc*<br/>
から文字列の作成に使用される要素を格納している safearray。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、または標準の HRESULT エラー値。

##  <a name="assignbstr"></a>  CComBSTR::AssignBSTR

は、BSTR を[m_str](#m_str)に割り当てます。

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>パラメーター

*bstrSrc*<br/>
から現在`CComBSTR`のオブジェクトに代入する BSTR。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、または標準の HRESULT エラー値。

##  <a name="attach"></a>CComBSTR:: Attach

[M_str](#m_str)メンバーを*src*に`CComBSTR`設定することによって、BSTR をオブジェクトにアタッチします。

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>パラメーター

*src*<br/>
からオブジェクトにアタッチする BSTR。

### <a name="remarks"></a>Remarks

通常のワイド文字列をこのメソッドに渡さないでください。 コンパイラはエラーをキャッチできず、実行時エラーが発生します。

> [!NOTE]
>  が NULL 以外の場合`m_str` 、このメソッドはをアサートします。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="bstrtoarray"></a>CComBSTR:: BSTRToArray

0から始まる1次元の safearray を作成します。配列の各要素は、 `CComBSTR`オブジェクトの文字です。

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>パラメーター

*ppArray*<br/>
入出力関数の結果を保持するために使用される safearray へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、または標準の HRESULT エラー値。

##  <a name="bytelength"></a>  CComBSTR::ByteLength

の`m_str`バイト数を返します (終端の null 文字は除く)。

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>戻り値

[M_str](#m_str)メンバーの長さ (バイト単位)。

### <a name="remarks"></a>Remarks

が NULL の`m_str`場合は0を返します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

##  <a name="ccombstr"></a>CComBSTR:: CComBSTR

コンストラクターです。 既定のコンストラクターは、 [m_str](#m_str)メンバーを NULL に設定します。

```
CComBSTR() throw();
CComBSTR(const CComBSTR& src);
CComBSTR(REFGUID  guid);
CComBSTR(int nSize);
CComBSTR(int nSize, LPCOLESTR sz);
CComBSTR(int nSize, LPCSTR sz);
CComBSTR(LPCOLESTR pSrc);
CComBSTR(LPCSTR pSrc);
CComBSTR(CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="parameters"></a>パラメーター

*nSize*<br/>
から*Sz*からコピーする文字数、またはの文字`CComBSTR`数の初期サイズ。

*sz*<br/>
[入力] コピーする文字列。 Unicode バージョンでは、LPCOLESTR が指定されています。ANSI バージョンでは、LPCSTR が指定されています。

*.Psrc*<br/>
[入力] コピーする文字列。 Unicode バージョンでは、LPCOLESTR が指定されています。ANSI バージョンでは、LPCSTR が指定されています。

*src*<br/>
[入力] `CComBSTR` オブジェクト。

*guid*<br/>
から`GUID`構造体への参照。

### <a name="remarks"></a>Remarks

コピーコンストラクターは、 `m_str` *src*の BSTR メンバーのコピーにを設定します。コンストラクター `REFGUID`はを使用して`StringFromGUID2` GUID を文字列に変換し、その結果を格納します。

その他のコンストラクターは、`m_str` を指定された文字列のコピーに設定します。 *NSize*の値を渡すと、 *nSize*文字だけがコピーされ、その後に終端の null 文字が続きます。

`CComBSTR` は移動セマンティクスをサポートします。 移動コンストラクター (右辺値参照 `&&` を取るコンストラクター) を使用して、オブジェクト コピーのオーバーヘッドなしに、引数として渡した古いオブジェクトと同一の基になるデータを使用する新しいオブジェクトを作成することができます。

デストラクターは、`m_str` が指す文字列を解放します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

##  <a name="dtor"></a>CComBSTR:: ~ CComBSTR

デストラクターです。

```
~CComBSTR();
```

### <a name="remarks"></a>Remarks

デストラクターは、`m_str` が指す文字列を解放します。

##  <a name="copy"></a>  CComBSTR::Copy

の`m_str`コピーを割り当てて返します。

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>戻り値

[M_str](#m_str)メンバーのコピー。 が`m_str` null の場合、は null を返します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

##  <a name="copyto"></a>  CComBSTR::CopyTo

パラメーターを使用して、 [m_str](#m_str)のコピーを割り当てて返します。

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>パラメーター

*pbstr*<br/>
入出力このメソッドによって割り当てられた文字列を返す BSTR のアドレス。

*pvarDest*<br/>
入出力このメソッドによって割り当てられた文字列を返すバリアントのアドレス。

### <a name="return-value"></a>戻り値

コピーの成功または失敗を示す標準の HRESULT 値。

### <a name="remarks"></a>Remarks

このメソッドを呼び出した後、 *pvarDest*が指すバリアントは VT_BSTR 型になります。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

##  <a name="detach"></a>  CComBSTR::Detach

`CComBSTR`オブジェクトから[m_str](#m_str)をデタッチし、 `m_str`を NULL に設定します。

```
BSTR Detach() throw();
```

### <a name="return-value"></a>戻り値

`CComBSTR`オブジェクトに関連付けられている BSTR。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

##  <a name="empty"></a>CComBSTR:: Empty

[M_str](#m_str)メンバーを解放します。

```
void Empty() throw();
```

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

##  <a name="length"></a>  CComBSTR::Length

の文字`m_str`数を返します (終端の null 文字は除く)。

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>戻り値

[M_str](#m_str)メンバーの長さ。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

##  <a name="loadstring"></a>  CComBSTR::LoadString

*NID*によって指定された文字列リソースを読み込み、このオブジェクトに格納します。

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>パラメーター

Windows SDK の「 [Loadstring](/windows/win32/api/winuser/nf-winuser-loadstringw) 」を参照してください。

### <a name="return-value"></a>戻り値

文字列が正常に読み込まれた場合は TRUE を返します。それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

最初の関数は、 *hInst*パラメーターを使用して、ユーザーが指定したモジュールからリソースを読み込みます。 2番目の関数は、このプロジェクトで使用されている[CComModule](../../atl/reference/ccommodule-class.md)派生オブジェクトに関連付けられているリソースモジュールからリソースを読み込みます。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

##  <a name="m_str"></a>CComBSTR:: m_str

`CComBSTR`オブジェクトに関連付けられている BSTR を格納します。

```
BSTR m_str;
```

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

##  <a name="operator_bstr"></a>CComBSTR:: operator BSTR

オブジェクトを`CComBSTR` BSTR にキャストします。

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Remarks

では、 `CComBSTR` **[in] BSTR**パラメーターを持つ関数にオブジェクトを渡すことができます。

### <a name="example"></a>例

[CComBSTR:: m_str](#m_str)の例を参照してください。

##  <a name="operator_not"></a>CComBSTR:: operator!

BSTR 文字列が NULL かどうかを確認します。

```
bool operator!() const throw();
```

### <a name="return-value"></a>戻り値

[M_str](#m_str)メンバーが NULL の場合に TRUE を返します。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

この演算子は、空の文字列ではなく、NULL 値のみをチェックします。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="operator_neq"></a>CComBSTR:: operator! =

[演算子 = =](#operator_eq_eq)と逆の論理和を返します。

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>パラメーター

*bstrSrc*<br/>
[入力] `CComBSTR` オブジェクト。

*pszSrc*<br/>
から0で終わる文字列。

*nNull*<br/>
からNULL にする必要があります。

### <a name="return-value"></a>戻り値

比較対象の項目が`CComBSTR`オブジェクトと等しくない場合は TRUE を返します。それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

`CComBSTR`は、ユーザーの既定のロケールのコンテキストでテキストと比較されます。 最後の比較演算子は、含まれている文字列を NULL と比較するだけです。

##  <a name="operator_amp"></a>CComBSTR:: operator&amp;

[M_str](#m_str)メンバーに格納されている BSTR のアドレスを返します。

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Remarks

`CComBstr operator &`には、メモリリークを識別できるように、関連付けられた特別なアサーションがあります。 `m_str`メンバーが初期化されると、プログラムはアサートします。 このアサーションは、プログラマがを使用して、 `& operator`の最初の`m_str`割り当てを解放せ`m_str`ずに新しい値をメンバーに割り当てる状況を識別するために作成されました。 が`m_str` NULL の場合、プログラムは、m_str がまだ割り当てられていないと想定します。 この場合、プログラムはアサートしません。

このアサーションは、既定では有効になっていません。 このアサーションを有効にするには、ATL_CCOMBSTR_ADDRESS_OF_ASSERT を定義します。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

##  <a name="operator_add_eq"></a>CComBSTR:: operator + =

`CComBSTR`オブジェクトに文字列を追加します。

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>パラメーター

*bstrSrc*<br/>
から追加`CComBSTR`するオブジェクト。

*pszSrc*<br/>
から追加する0で終わる文字列。

### <a name="remarks"></a>Remarks

`CComBSTR`は、ユーザーの既定のロケールのコンテキストでテキストと比較されます。 LPCOLESTR の比較は、各`memcmp`文字列の生データに対してを使用して行われます。 LPCSTR の比較は、 *Pszsrc*の一時的な Unicode コピーが作成されたときと同じ方法で実行されます。 最後の比較演算子は、含まれている文字列を NULL と比較するだけです。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

##  <a name="operator_lt"></a>CComBSTR:: operator&lt;

と`CComBSTR`文字列を比較します。

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>戻り値

比較対象の項目が`CComBSTR`オブジェクトより小さい場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

比較は、ユーザーの既定のロケールを使用して実行されます。

##  <a name="operator_eq"></a>CComBSTR:: operator =

[M_str](#m_str)メンバーを、 *psrc*のコピー、または*src*の BSTR メンバーのコピーに設定します。移動代入演算子は、 `src`コピーせずに移動します。

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Remarks

*Psrc*パラメーターは、Unicode バージョンの場合は LPCOLESTR、ANSI バージョンの場合は LPCSTR を指定します。

### <a name="example"></a>例

[CComBSTR:: Copy](#copy)の例を参照してください。

##  <a name="operator_eq_eq"></a>  CComBSTR::operator ==

と`CComBSTR`文字列を比較します。 `CComBSTR`は、ユーザーの既定のロケールのコンテキストでテキストと比較されます。

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>パラメーター

*bstrSrc*<br/>
[入力] `CComBSTR` オブジェクト。

*pszSrc*<br/>
から0で終わる文字列。

*nNull*<br/>
からNULL にする必要があります。

### <a name="return-value"></a>戻り値

比較対象の項目が`CComBSTR`オブジェクトと等しい場合は TRUE を返します。それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

最後の比較演算子は、含まれている文字列を NULL と比較するだけです。

##  <a name="operator_gt"></a>CComBSTR:: operator&gt;

と`CComBSTR`文字列を比較します。

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>戻り値

比較対象の項目が`CComBSTR`オブジェクトより大きい場合は TRUE を返します。それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

比較は、ユーザーの既定のロケールを使用して実行されます。

##  <a name="readfromstream"></a>  CComBSTR::ReadFromStream

[M_str](#m_str)メンバーを、指定したストリームに格納されている BSTR に設定します。

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>パラメーター

*pStream*<br/>
からデータを格納しているストリームの[IStream](/windows/win32/api/objidl/nn-objidl-istream)インターフェイスへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

`ReadToStream`[Writetostream](#writetostream)への呼び出しによって書き込まれたデータ形式との互換性を確保するために、ストリームの内容を現在の位置に配置する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

##  <a name="tolower"></a>  CComBSTR::ToLower

含まれている文字列を小文字に変換します。

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

変換`CharLowerBuff`の実行方法の詳細については、「」を参照してください。

##  <a name="toupper"></a>CComBSTR:: ToUpper

含まれている文字列を大文字に変換します。

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

変換`CharUpperBuff`の実行方法の詳細については、「」を参照してください。

##  <a name="writetostream"></a>CComBSTR:: WriteToStream

[M_str](#m_str)メンバーをストリームに保存します。

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>パラメーター

*pStream*<br/>
からストリームの[IStream](/windows/win32/api/objidl/nn-objidl-istream)インターフェイスへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

[Readfromstream](#readfromstream)関数を使用して、ストリームのコンテンツから BSTR を再作成することができます。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)<br/>
[ATL および MFC 文字列変換マクロ](string-conversion-macros.md)
