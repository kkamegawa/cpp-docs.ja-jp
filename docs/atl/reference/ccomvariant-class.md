---
title: CComVariant クラス
ms.date: 11/04/2016
f1_keywords:
- CComVariant
- ATLCOMCLI/ATL::CComVariant
- ATLCOMCLI/ATL::CComVariant::CComVariant
- ATLCOMCLI/ATL::CComVariant::Attach
- ATLCOMCLI/ATL::CComVariant::ChangeType
- ATLCOMCLI/ATL::CComVariant::Clear
- ATLCOMCLI/ATL::CComVariant::Copy
- ATLCOMCLI/ATL::CComVariant::CopyTo
- ATLCOMCLI/ATL::CComVariant::Detach
- ATLCOMCLI/ATL::CComVariant::GetSize
- ATLCOMCLI/ATL::CComVariant::ReadFromStream
- ATLCOMCLI/ATL::CComVariant::SetByRef
- ATLCOMCLI/ATL::CComVariant::WriteToStream
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
ms.openlocfilehash: b4c157435aaffab5f1315fd4636f55f9d4e0d5b4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496860"
---
# <a name="ccomvariant-class"></a>CComVariant クラス

このクラスは、格納されているデータの型を示すメンバーを提供して、バリアント型をラップします。

## <a name="syntax"></a>構文

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CComVariant:: CComVariant](#ccomvariant)|コンストラクターです。|
|[CComVariant:: ~ CComVariant](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComVariant:: Attach](#attach)|`CComVariant`オブジェクトにバリアントをアタッチします。|
|[CComVariant:: ChangeType](#changetype)|`CComVariant`オブジェクトを新しい型に変換します。|
|[CComVariant:: Clear](#clear)|オブジェクトを`CComVariant`クリアします。|
|[CComVariant:: Copy](#copy)|`CComVariant`オブジェクトにバリアントをコピーします。|
|[CComVariant:: CopyTo](#copyto)|`CComVariant`オブジェクトの内容をコピーします。|
|[CComVariant::D etach](#detach)|基になるバリアントを`CComVariant`オブジェクトからデタッチします。|
|[CComVariant:: GetSize](#getsize)|`CComVariant`オブジェクトのコンテンツのサイズをバイト数で返します。|
|[CComVariant:: ReadFromStream](#readfromstream)|ストリームからバリアントを読み込みます。|
|[CComVariant::SetByRef](#setbyref)|オブジェクトを初期化し、 `vt`メンバーを VT_BYREF に設定します。 `CComVariant`|
|[CComVariant:: WriteToStream](#writetostream)|基になるバリアントをストリームに保存します。|

### <a name="public-operators"></a>パブリック演算子

|||
|-|-|
|[CComVariant:: operator <](#operator_lt)|`CComVariant`オブジェクトが、指定されたバリアントより小さいかどうかを示します。|
|[CComVariant:: operator >](#operator_gt)|`CComVariant`オブジェクトが、指定されたバリアントよりも大きいかどうかを示します。|
|[operator !=](#operator_neq)|`CComVariant`オブジェクトが、指定されたバリアントと等しくないかどうかを示します。|
|[operator=](#operator_eq)|`CComVariant`オブジェクトに値を割り当てます。|
|[operator ==](#operator_eq_eq)|オブジェクトが`CComVariant`指定されたバリアントと等しいかどうかを示します。|

## <a name="remarks"></a>Remarks

`CComVariant`union と、共用体に格納されているデータの型を示すメンバーで構成される、バリアント型と VARIANTARG 型をラップします。 バリアントは通常、オートメーションで使用されます。

`CComVariant`variant 型から派生して、バリアントを使用できる場所で使用できるようにします。 たとえば、V_VT マクロを使用しての`CComVariant`型を抽出したり、バリアントと同様にメンバーに`vt`直接アクセスしたりすることができます。

## <a name="inheritance-hierarchy"></a>継承階層

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcomcli. h

##  <a name="attach"></a>  CComVariant::Attach

`CComVariant`オブジェクトの現在の内容を安全にクリアし、 *psrc*の内容をこのオブジェクトにコピーして、バリアント型*psrc*を VT_EMPTY に設定します。

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>パラメーター

*.Psrc*<br/>
からオブジェクトにアタッチされる[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)を指します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

*Psrc*によって保持されているデータの`CComVariant`所有権は、オブジェクトに転送されます。

##  <a name="ccomvariant"></a>CComVariant:: CComVariant

各コンストラクターは、 `CComVariant` `VariantInit` Win32 関数を呼び出すか、渡されたパラメーターに従ってオブジェクトの値と型を設定することによって、オブジェクトの安全な初期化を処理します。

```
CComVariant() throw();
CComVariant(const CComVariant& varSrc);
CComVariant(const VARIANT& varSrc);
CComVariant(LPCOLESTR lpszSrc);
CComVariant(LPCSTR lpszSrc);
CComVariant(bool bSrc);
CComVariant(BYTE nSrc) throw();
CComVariant(int nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned int  nSrc, VARTYPE vtSrc = VT_UI4) throw();
CComVariant(shor  nSrc) throw();
CComVariant(unsigned short nSrc) throw();
CComVariant(long  nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned long  nSrc) throw();
CComVariant(LONGLONG  nSrc) throw();
CComVariant(ULONGLONG  nSrc) throw();
CComVariant(float  fltSrc) throw();
CComVariant(double  dblSrc, VARTYPE vtSrc = VT_R8) throw();
CComVariant(CY  cySrc) throw();
CComVariant(IDispatch* pSrc) throw();
CComVariant(IUnknown* pSrc) throw();
CComVariant(const SAFEARRAY* pSrc);
CComVariant(char  cSrc) throw();
CComVariant(const CComBSTR& bstrSrc);
```

### <a name="parameters"></a>パラメーター

*varSrc*<br/>
からオブジェクトの`CComVariant`初期化に使用されるまたはバリアント。`CComVariant` 変換元バリアントの内容は変換せずにコピー先にコピーされます。

*lpszSrc*<br/>
からオブジェクトの`CComVariant`初期化に使用される文字列。 0で終わるワイド (Unicode) 文字列をコンストラクターの LPCOLESTR バージョンに渡すことも、ANSI 文字列を LPCSTR バージョンに渡すこともできます。 どちらの場合も、文字列はを使用して`SysAllocString`割り当てられた Unicode BSTR に変換されます。 `CComVariant`オブジェクトの型は VT_BSTR になります。

*bSrc*<br/>
からオブジェクトの`CComVariant`初期化に使用されるブール値。 **ブール**型の引数は、格納される前に VARIANT_BOOL に変換されます。 `CComVariant`オブジェクトの型は VT_BOOL になります。

*nSrc*<br/>
からオブジェクトの初期化に使用される int、BYTE、short、long、longlong、ULONGLONG、unsigned short、unsigned long、または unsigned int。 `CComVariant` `CComVariant`オブジェクトの型は、それぞれ VT_I4、VT_UI1、VT_I2、VT_I4、VT_I8、VT_UI8、VT_UI2、VT_UI4、または VT_UI4 になります。

*vtSrc*<br/>
からバリアントの型。 最初のパラメーターが**int**の場合、有効な型は VT_I4 と VT_INT です。 最初のパラメーターが**long**の場合、有効な型は VT_I4 と VT_ERROR です。 最初のパラメーターが**double**の場合、有効な型は VT_R8 と VT_DATE です。 最初のパラメーターが**unsigned int**の場合、有効な型は VT_UI4 と VT_UINT です。

*fltSrc*<br/>
からオブジェクトの`CComVariant`初期化に使用される float。 `CComVariant`オブジェクトの型は VT_R4 になります。

*dblSrc*<br/>
からオブジェクトの`CComVariant`初期化に使用される double。 `CComVariant`オブジェクトの型は VT_R8 になります。

*cySrc*<br/>
からオブジェクトを`CComVariant`初期化するために`CY`使用する。 `CComVariant`オブジェクトの型は VT_CY になります。

*.Psrc*<br/>
からオブジェクトの`IUnknown` `IDispatch` 初期`CComVariant`化に使用されるポインターまたはポインター。 `AddRef`は、インターフェイスポインターで呼び出されます。 `CComVariant`オブジェクトの型は、それぞれ VT_DISPATCH または VT_UNKNOWN になります。

または、オブジェクトの`CComVariant`初期化に使用される、saf のポインターです。 SAFEARRAY のコピーは、 `CComVariant`オブジェクトに格納されます。 `CComVariant`オブジェクトの型は、SAFEARRAY と VT_ARRAY の元の型を組み合わせたものになります。

*cSrc*<br/>
からオブジェクトの`CComVariant`初期化に使用される文字。 `CComVariant`オブジェクトの型は VT_I1 になります。

*bstrSrc*<br/>
からオブジェクトの`CComVariant`初期化に使用される BSTR。 `CComVariant`オブジェクトの型は VT_BSTR になります。

### <a name="remarks"></a>Remarks

デストラクターは、 [CComVariant:: Clear](#clear)を呼び出すことによってクリーンアップを管理します。

##  <a name="dtor"></a>CComVariant:: ~ CComVariant

デストラクターです。

```
~CComVariant() throw();
```

### <a name="remarks"></a>Remarks

このメソッド[は、CComVariant:: Clear](#clear)を呼び出すことによってクリーンアップを管理します。

##  <a name="changetype"></a>  CComVariant::ChangeType

`CComVariant`オブジェクトを新しい型に変換します。

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>パラメーター

*vtNew*<br/>
から`CComVariant`オブジェクトの新しい型。

*.Psrc*<br/>
から値が新しい型に変換されるバリアントへのポインター。 既定値は NULL です。これは`CComVariant` 、オブジェクトが代わりに変換されることを意味します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

*Psrc*に値を渡すと、 `ChangeType`はこのバリアントを変換のソースとして使用します。 それ以外の場合は、オブジェクトがソースになります。`CComVariant`

##  <a name="clear"></a>CComVariant:: Clear

`VariantClear` Win32 関数`CComVariant`を呼び出すことによって、オブジェクトをクリアします。

```
HRESULT Clear();
```

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

デストラクターは自動的に`Clear`を呼び出します。

##  <a name="copy"></a>  CComVariant::Copy

`CComVariant`オブジェクトを解放し、指定したバリアントのコピーを割り当てます。

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>パラメーター

*.Psrc*<br/>
からコピーされる[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)へのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="copyto"></a>  CComVariant::CopyTo

`CComVariant`オブジェクトの内容をコピーします。

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>パラメーター

*pstrDest*<br/>
`CComVariant`オブジェクトの内容のコピーを受け取る BSTR を指します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

オブジェクト`CComVariant`は VT_BSTR 型である必要があります。

##  <a name="detach"></a>CComVariant::D etach

基になるバリアントを`CComVariant`オブジェクトからデタッチし、オブジェクトの型を VT_EMPTY に設定します。

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>パラメーター

*pDest*<br/>
入出力オブジェクトの基になるバリアント値を返します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

*Pdest*によって参照されるバリアントの内容は、呼び出し元`CComVariant`のオブジェクトの値と型が割り当てられる前に自動的にクリアされることに注意してください。

##  <a name="getsize"></a>CComVariant:: GetSize

単純固定サイズのバリアントの場合、このメソッドは、基になるデータ型と**sizeof (VARTYPE)** の**sizeof**を返します。

```
ULONG GetSize() const;
```

### <a name="return-value"></a>戻り値

`CComVariant`オブジェクトの現在のコンテンツのサイズ (バイト単位)。

### <a name="remarks"></a>Remarks

バリアントにインターフェイスポインターが含まれて`GetSize`いる場合`IPersistStream`は`IPersistStreamInit`、またはに対してクエリを行います。 成功した場合、戻り値は、によって`GetSizeMax`返される値の下位32ビット、および**sizeof** a CLSID および**sizeof (VARTYPE)** です。 インターフェイスポインターが NULL の場合、 `GetSize`によって、 **sizeof**と**sizeof (VARTYPE)** が返されます。 合計サイズが ULONG_MAX より大きい場合は、 `GetSize`エラーを示す**sizeof (VARTYPE)** を返します。

それ以外の場合は、VT_BSTR 型の一時的な VARIANT が現在のバリアントから強制されます。 この BSTR の長さは、文字列の長さと文字列自体の長さに加え、null 文字と**sizeof (VARTYPE)** のサイズを加算した値として計算されます。 バリアントを VT_BSTR 型のバリアントに強制的に変換できない場合`GetSize` 、は**sizeof (VARTYPE)** を返します。

このメソッドによって返されるサイズは、正常な条件下で[CComVariant:: WriteToStream](#writetostream)によって使用されるバイト数と一致します。

##  <a name="operator_eq"></a>CComVariant:: operator =

`CComVariant`オブジェクトに値と対応する型を割り当てます。

```
CComVariant& operator=(const CComVariant& varSrc);
CComVariant& operator=(const VARIANT& varSrc);
CComVariant& operator=(const CComBSTR& bstrSrc);
CComVariant& operator=(LPCOLESTR lpszSrc);
CComVariant& operator=(LPCSTR lpszSrc);
CComVariant& operator=(bool bSrc);
CComVariant& operator=(BYTE nSrc) throw();
CComVariant& operator=int nSrc) throw();
CComVariant& operator=(unsigned int nSrc) throw();
CComVariant& operator=(short nSrc) throw();
CComVariant& operator=(unsigned short nSrc) throw();
CComVariant& operator=(long nSrc) throw();
CComVariant& operator=(unsigned long nSrc) throw();
CComVariant& operator=(LONGLONG nSrc) throw();
CComVariant& operator=(ULONGLONG nSrc) throw();
CComVariant& operator=(float fltSrc) throw();
CComVariant& operator=(double dblSrc) throw();
CComVariant& operator=(CY cySrc) throw();
CComVariant& operator=(IDispatch* pSrc) throw();
CComVariant& operator=(IUnknown* pSrc) throw();
CComVariant& operator=(const SAFEARRAY* pSrc);
CComVariant& operator=(char cSrc) throw();
```

### <a name="parameters"></a>パラメーター

*varSrc*<br/>
からオブジェクトに割り当てら`CComVariant`れるまた`CComVariant`は [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)。 変換元バリアントの内容は変換せずにコピー先にコピーされます。

*bstrSrc*<br/>
から`CComVariant`オブジェクトに割り当てられる BSTR。 `CComVariant`オブジェクトの型は VT_BSTR になります。

*lpszSrc*<br/>
から`CComVariant`オブジェクトに割り当てられる文字列。 0で終わるワイド (Unicode) 文字列を演算子の LPCOLESTR バージョンに渡すことも、ANSI 文字列を LPCSTR バージョンに渡すこともできます。 どちらの場合も、文字列はを使用して`SysAllocString`割り当てられた Unicode BSTR に変換されます。 `CComVariant`オブジェクトの型は VT_BSTR になります。

*bSrc*<br/>
から`CComVariant`オブジェクトに割り当てられる**ブール**値。 **ブール**型の引数は、格納される前に VARIANT_BOOL に変換されます。 `CComVariant`オブジェクトの型は VT_BOOL になります。

*nSrc*<br/>
からオブジェクト`CComVariant`に割り当てる**int**、BYTE、 **short**、 **long**、longlong、ULONGLONG、 **unsigned short**、 **unsigned long**、または**unsigned int** 。 `CComVariant`オブジェクトの型は、それぞれ VT_I4、VT_UI1、VT_I2、VT_I4、VT_I8、VT_UI8、VT_UI2、VT_UI4、または VT_UI4 になります。

*fltSrc*<br/>
から`CComVariant`オブジェクトに割り当てられる**float** 。 `CComVariant`オブジェクトの型は VT_R4 になります。

*dblSrc*<br/>
から`CComVariant`オブジェクトに割り当てられる**倍精度浮動小数点数**。 `CComVariant`オブジェクトの型は VT_R8 になります。

*cySrc*<br/>
からオブジェクトに`CComVariant`割り当てられる。 `CY` `CComVariant`オブジェクトの型は VT_CY になります。

*.Psrc*<br/>
からオブジェクトに`CComVariant`割り当てられるポインター `IUnknown`またはポインター `IDispatch` 。 `AddRef`は、インターフェイスポインターで呼び出されます。 `CComVariant`オブジェクトの型は、それぞれ VT_DISPATCH または VT_UNKNOWN になります。

または、 `CComVariant`オブジェクトに割り当てられる SAFEARRAY ポインター。 SAFEARRAY のコピーは、 `CComVariant`オブジェクトに格納されます。 `CComVariant`オブジェクトの型は、SAFEARRAY と VT_ARRAY の元の型を組み合わせたものになります。

*cSrc*<br/>
から`CComVariant`オブジェクトに割り当てられる char。 `CComVariant`オブジェクトの型は VT_I1 になります。

##  <a name="operator_eq_eq"></a>CComVariant:: operator = =

オブジェクトが`CComVariant`指定されたバリアントと等しいかどうかを示します。

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Remarks

*Varsrc*の値と型が、 `CComVariant`オブジェクトの値と型にそれぞれ等しい場合に TRUE を返します。 それ以外の場合は FALSE。 演算子は、ユーザーの既定のロケールを使用して比較を実行します。

演算子は、バリアント型の値のみを比較します。 これは、文字列、整数、および浮動小数点を比較しますが、配列やレコードは比較しません。

##  <a name="operator_neq"></a>CComVariant:: operator! =

`CComVariant`オブジェクトが、指定されたバリアントと等しくないかどうかを示します。

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Remarks

*Varsrc*の値または型が、それぞれ`CComVariant`オブジェクトの値または型と等しくない場合に TRUE を返します。 それ以外の場合は FALSE。 演算子は、ユーザーの既定のロケールを使用して比較を実行します。

演算子は、バリアント型の値のみを比較します。 これは、文字列、整数、および浮動小数点を比較しますが、配列やレコードは比較しません。

##  <a name="operator_lt"></a>CComVariant:: operator&lt;

`CComVariant`オブジェクトが、指定されたバリアントより小さいかどうかを示します。

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Remarks

`CComVariant`オブジェクトの値が*varsrc*の値より小さい場合に TRUE を返します。 それ以外の場合は FALSE。 演算子は、ユーザーの既定のロケールを使用して比較を実行します。

##  <a name="operator_gt"></a>CComVariant:: operator&gt;

`CComVariant`オブジェクトが、指定されたバリアントよりも大きいかどうかを示します。

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Remarks

`CComVariant`オブジェクトの値が*varsrc*の値より大きい場合に TRUE を返します。 それ以外の場合は FALSE。 演算子は、ユーザーの既定のロケールを使用して比較を実行します。

##  <a name="readfromstream"></a>  CComVariant::ReadFromStream

基になるバリアントを、指定したストリームに格納されているバリアントに設定します。

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>パラメーター

*pStream*<br/>
からデータを格納しているストリームの[IStream](/windows/win32/api/objidl/nn-objidl-istream)インターフェイスへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

`ReadToStream`[Writetostream](#writetostream)に対する以前の呼び出しが必要です。

##  <a name="setbyref"></a>CComVariant:: SetByRef

オブジェクトを初期化し、 `vt`メンバーを VT_BYREF に設定します。 `CComVariant`

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>パラメーター

*T*<br/>
バリアントの型 (BSTR、 **int**、 **char**など)。

*未満*<br/>
`CComVariant`オブジェクトを初期化するために使用するポインター。

### <a name="remarks"></a>Remarks

`SetByRef`は、 `CComVariant`オブジェクトをポインター*ポイント*に初期化し、 `vt`メンバーを VT_BYREF に設定する関数テンプレートです。 例:

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

##  <a name="writetostream"></a>CComVariant:: WriteToStream

基になるバリアントをストリームに保存します。

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>パラメーター

*pStream*<br/>
からストリームの[IStream](/windows/win32/api/objidl/nn-objidl-istream)インターフェイスへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
