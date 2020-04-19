---
title: COleVariant クラス
ms.date: 11/04/2016
f1_keywords:
- COleVariant
- AFXDISP/COleVariant
- AFXDISP/COleVariant::COleVariant
- AFXDISP/COleVariant::Attach
- AFXDISP/COleVariant::ChangeType
- AFXDISP/COleVariant::Clear
- AFXDISP/COleVariant::Detach
- AFXDISP/COleVariant::GetByteArrayFromVariantArray
- AFXDISP/COleVariant::SetString
helpviewer_keywords:
- COleVariant [MFC], COleVariant
- COleVariant [MFC], Attach
- COleVariant [MFC], ChangeType
- COleVariant [MFC], Clear
- COleVariant [MFC], Detach
- COleVariant [MFC], GetByteArrayFromVariantArray
- COleVariant [MFC], SetString
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
ms.openlocfilehash: 49cd4a8d3db436d5e3c4d29efbb4d80b4741a270
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739791"
---
# <a name="colevariant-class"></a>COleVariant クラス

[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) データ型をカプセル化します。

## <a name="syntax"></a>構文

```
class COleVariant : public tagVARIANT
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleVariant:: COleVariant](#colevariant)|`COleVariant` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleVariant:: Attach](#attach)|バリアントをに`COleVariant`結び付けます。|
|[COleVariant:: ChangeType](#changetype)|この`COleVariant`オブジェクトのバリアント型を変更します。|
|[COleVariant:: Clear](#clear)|この`COleVariant`オブジェクトをクリアします。|
|[COleVariant::D etach](#detach)|から`COleVariant` variant を切り離し、バリアントを返します。|
|[COleVariant:: GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|既存の variant 配列からバイト配列を取得します。|
|[COleVariant:: SetString](#setstring)|文字列を特定の型 (通常は ANSI) に設定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[COleVariant:: operator LPCVARIANT](#operator_lpcvariant)|`COleVariant` 値`LPCVARIANT`をに変換します。|
|[COleVariant:: operator LPVARIANT](#operator_lpvariant)|`COleVariant` オブジェクト`LPVARIANT`をに変換します。|
|[COleVariant:: operator =](#operator_eq)|値を`COleVariant`コピーします。|
|[COleVariant:: operator = =](#operator_eq_eq)|2つ`COleVariant`の値を比較します。|
|[COleVariant:: operator &lt;、 &lt;&gt;&gt;](#operator_lt_lt__gt_gt)|`CArchive` `COleVariant`値をまたは`CArchive` `CDumpContext`に出力し、からオブジェクトを入力します。 `COleVariant`|

## <a name="remarks"></a>Remarks

このデータ型は、OLE オートメーションで使用されます。 具体的には、 [Dispparams](/windows/win32/api/oaidl/ns-oaidl-dispparams)構造体には、VARIANT 構造体の配列へのポインターが含まれています。 構造`DISPPARAMS`体は、パラメーターを[IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)に渡すために使用されます。

> [!NOTE]
> このクラスは、 `VARIANT`構造体から派生します。 これ`COleVariant`は、を呼び出す`VARIANT`パラメーターでを渡すことができ、 `VARIANT`構造体のデータメンバーがの`COleVariant`アクセス可能なデータメンバーであることを意味します。

2つの関連する MFC クラス[COleCurrency](../../mfc/reference/colecurrency-class.md)および[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)は、variant データ型`VT_CY`CURRENCY () と`VT_DATE`DATE () をカプセル化します。 `COleVariant` クラスは、DAO クラスで広く使用されています。このクラスの一般的な使用方法については、[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) や [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) などのクラスを参照してください。

詳細については、Windows SDK の「 [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)」、「 [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1)」、「 [Dispparams](/windows/win32/api/oaidl/ns-oaidl-dispparams)」、および「 [IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)エントリ」を参照してください。

クラスの`COleVariant`詳細および ole オートメーションでの使用方法については、記事「[オートメーション](../../mfc/automation.md)」の「ole オートメーションでのパラメーターの引き渡し」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

##  <a name="attach"></a>COleVariant:: Attach

この関数を呼び出して、指定した[バリアント](/windows/win32/api/oaidl/ns-oaidl-variant)オブジェクトを`COleVariant`現在のオブジェクトにアタッチします。

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>パラメーター

*varSrc*<br/>
`VARIANT` 現在`COleVariant`のオブジェクトにアタッチする既存のオブジェクト。

### <a name="remarks"></a>Remarks

この関数は、 *Varsrc*の VARTYPE を VT_EMPTY に設定します。

詳細については、Windows SDK の[バリアント](/windows/win32/api/oaidl/ns-oaidl-variant)と[varenum](/windows/win32/api/wtypes/ne-wtypes-varenum)のエントリを参照してください。

##  <a name="colevariant"></a>COleVariant:: COleVariant

`COleVariant` オブジェクトを構築します。

```
COleVariant();
COleVariant(const VARIANT& varSrc);
COleVariant(const COleVariant& varSrc);
COleVariant(LPCVARIANT pSrc);
COleVariant(LPCTSTR lpszSrc);
COleVariant(LPCTSTR lpszSrc, VARTYPE vtSrc);
COleVariant(CString& strSrc);
COleVariant(BYTE nSrc);
COleVariant(short nSrc, VARTYPE vtSrc = VT_I2);
COleVariant(long lSrc,VARTYPE vtSrc = VT_I4);
COleVariant(const COleCurrency& curSrc);
COleVariant(float fltSrc);
COleVariant(double dblSrc);
COleVariant(const COleDateTime& timeSrc);
COleVariant(const CByteArray& arrSrc);
COleVariant(const CLongBinary& lbSrc);
COleVariant(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>パラメーター

*varSrc*<br/>
新しい`VARIANT` `COleVariant` オブジェクトにコピーされる既存の`COleVariant`またはオブジェクト。

*.Psrc*<br/>
`VARIANT` 新しい`COleVariant`オブジェクトにコピーされるオブジェクトへのポインター。

*lpszSrc*<br/>
新しい`COleVariant`オブジェクトにコピーされる null で終わる文字列。

*vtSrc*<br/>
`VARTYPE` 新しい`COleVariant`オブジェクトの。

*strSrc*<br/>
新しい`COleVariant`オブジェクトにコピーされる[CString](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクト。

*nSrc*、 *lsrc*新しい`COleVariant`オブジェクトにコピーする数値。

*vtSrc*<br/>
`VARTYPE` 新しい`COleVariant`オブジェクトの。

*curSrc*<br/>
新しい`COleVariant`オブジェクトにコピーされる[COleCurrency](../../mfc/reference/colecurrency-class.md)オブジェクト。

*Fltsrc*、 *dblsrc*<br/>
新しい `COleVariant` オブジェクトにコピーされる数値。

*timeSrc*<br/>
新しい`COleVariant`オブジェクトにコピーされる[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクト。

*arrSrc*<br/>
新しい`COleVariant`オブジェクトにコピーされる[CByteArray](../../mfc/reference/cbytearray-class.md)オブジェクト。

*lbSrc*<br/>
新しい`COleVariant`オブジェクトにコピーされる[CLongBinary](../../mfc/reference/clongbinary-class.md)オブジェクト。

*pidl*<br/>
新しい`COleVariant`オブジェクトにコピーされる[itemidlist](/windows/win32/api/shtypes/ns-shtypes-itemidlist)構造体へのポインター。

### <a name="remarks"></a>Remarks

これらのすべてのコンストラクター `COleVariant`は、指定された値に初期化された新しいオブジェクトを作成します。 これらの各コンストラクターの簡単な説明を次に示します。

- **COleVariant ()** 空`COleVariant`のオブジェクト VT_EMPTY を作成します。

- **COleVariant (** *varsrc* **)** 既存`VARIANT`のまたは`COleVariant`オブジェクトをコピーします。 バリアント型は保持されます。

- **COleVariant (** *psrc* **)** 既存`VARIANT`のまたは`COleVariant`オブジェクトをコピーします。 バリアント型は保持されます。

- **COleVariant (** *lpszsrc* **)** 新しいオブジェクト VT_BSTR (UNICODE) に文字列をコピーします。

- **COleVariant (** *lpszsrc* **、** *vtsrc* **)** 新しいオブジェクトに文字列をコピーします。 *Vtsrc*のパラメーターには、VT_BSTR (UNICODE) または VT_BSTRT (ANSI) を指定する必要があります。

- **COleVariant (** *strsrc* **)** 新しいオブジェクト VT_BSTR (UNICODE) に文字列をコピーします。

- **COleVariant (** *nSrc* **)** 新しいオブジェクト VT_UI1 に8ビットの整数をコピーします。

- **COleVariant (** *nSrc* **、** *vtsrc* **)** 新しいオブジェクトに16ビット整数 (またはブール値) をコピーします。 パラメーター *Vtsrc*は、VT_I2 または VT_BOOL である必要があります。

- **COleVariant (** *lsrc* **、** *vtsrc* **)** 32ビット整数 (または SCODE 値) を新しいオブジェクトにコピーします。 パラメーター *Vtsrc*は、VT_I4、VT_ERROR、または VT_BOOL である必要があります。

- **COleVariant (** *cursrc* **)** 新しいオブジェクト`COleCurrency` VT_CY に値をコピーします。

- **COleVariant (** *fltsrc* **)** 新しいオブジェクト VT_R4 に32ビット浮動小数点値をコピーします。

- **COleVariant (** *dblsrc* **)** 新しいオブジェクト VT_R8 に64ビット浮動小数点値をコピーします。

- **COleVariant (** *timesrc* **)** 新しいオブジェクト`COleDateTime` VT_DATE に値をコピーします。

- **COleVariant (** *arrsrc* **)** 新しいオブジェクト VT_EMPTY にオブジェクトをコピーします。`CByteArray`

- **COleVariant (** *lbSrc* **)** 新しいオブジェクト VT_EMPTY にオブジェクトをコピーします。`CLongBinary`

SCODE の詳細については、「Windows SDK の[COM エラーコードの構造](/windows/win32/com/structure-of-com-error-codes)」を参照してください。

##  <a name="changetype"></a>COleVariant:: ChangeType

この`COleVariant`オブジェクトのバリアント値の型を変換します。

```
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>パラメーター

*vartype*<br/>
この`COleVariant`オブジェクトの VARTYPE。

*.Psrc*<br/>
変換する[バリアント](/windows/win32/api/oaidl/ns-oaidl-variant)オブジェクトへのポインター。 この値が NULL の場合、 `COleVariant`このオブジェクトは変換のソースとして使用されます。

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の「 [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)」、「 [varenum](/windows/win32/api/wtypes/ne-wtypes-varenum)」、および「 [VariantChangeType](/windows/win32/api/oleauto/nf-oleauto-variantchangetype) 」の各エントリを参照してください。

##  <a name="clear"></a>COleVariant:: Clear

`VARIANT` を消去します。

```
void Clear();
```

### <a name="remarks"></a>Remarks

これにより、このオブジェクトの VARTYPE が VT_EMPTY に設定されます。 デストラクター `COleVariant`は、この関数を呼び出します。

詳細については、 `VARIANT`Windows SDK の、VARTYPE `VariantClear` 、およびエントリを参照してください。

##  <a name="detach"></a>COleVariant::D etach

基になる[バリアント](/windows/win32/api/oaidl/ns-oaidl-variant)オブジェクトをこの`COleVariant`オブジェクトからデタッチします。

```
VARIANT Detach();
```

### <a name="remarks"></a>Remarks

この関数は、この`COleVariant`オブジェクトの VARTYPE を VT_EMPTY に設定します。

> [!NOTE]
>  を呼び出し`Detach`た後、結果`VARIANT`の構造体に対し`VariantClear`てを呼び出すのは呼び出し元の責任です。

詳細については、Windows SDK の「 [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)」、「 [varenum](/windows/win32/api/wtypes/ne-wtypes-varenum)」、および「 [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) 」の各エントリを参照してください。

##  <a name="getbytearrayfromvariantarray"></a>COleVariant:: GetByteArrayFromVariantArray

既存の variant 配列からバイト配列を取得します。

```
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>パラメーター

*メモリ*<br/>
既存の[CByteArray](../../mfc/reference/cbytearray-class.md)オブジェクトへの参照。

##  <a name="operator_lpcvariant"></a>COleVariant:: operator LPCVARIANT

このキャスト演算子は、 `VARIANT`この`COleVariant`オブジェクトから値がコピーされる構造体を返します。

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>Remarks

##  <a name="operator_lpvariant"></a>COleVariant:: operator LPVARIANT

このキャスト演算子を呼び出して、この`VARIANT` `COleVariant`オブジェクトの基になる構造体にアクセスします。

```
operator LPVARIANT();
```

### <a name="remarks"></a>Remarks

> [!CAUTION]
> この関数によって`VARIANT`返されるポインターによってアクセスされる構造体の値を変更`COleVariant`すると、このオブジェクトの値が変更されます。

##  <a name="operator_eq"></a>COleVariant:: operator =

これらのオーバーロードされた代入演算子は、 `COleVariant` source 値をこのオブジェクトにコピーします。

```
const COleVariant& operator=(const VARIANT& varSrc);
const COleVariant& operator=(LPCVARIANT pSrc);
const COleVariant& operator=(const COleVariant& varSrc);
const COleVariant& operator=(const LPCTSTR lpszSrc);
const COleVariant& operator=(const CString& strSrc);
const COleVariant& operator=(BYTE nSrc);
const COleVariant& operator=(short nSrc);
const COleVariant& operator=(long lSrc);
const COleVariant& operator=(const COleCurrency& curSrc);
const COleVariant& operator=(float fltSrc);
const COleVariant& operator=(double dblSrc);
const COleVariant& operator=(const COleDateTime& dateSrc);
const COleVariant& operator=(const CByteArray& arrSrc);
const COleVariant& operator=(const CLongBinary& lbSrc);
```

### <a name="remarks"></a>Remarks

各演算子の簡単な説明を次に示します。

- **operator = (** *varsrc* **)** 既存のバリアントまたは`COleVariant`オブジェクトをこのオブジェクトにコピーします。

- **operator = (** *psrc* **)** *Psrc*によってアクセスされるバリアントオブジェクトをこのオブジェクトにコピーします。

- **operator = (** *lpszsrc* **)** Null で終わる文字列をこのオブジェクトにコピーし、VARTYPE を VT_BSTR に設定します。

- **operator = (** *strsrc* **)** [CString](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクトをこのオブジェクトにコピーし、VARTYPE を VT_BSTR に設定します。

- **operator = (** *nSrc* **)** 8ビットまたは16ビットの整数値をこのオブジェクトにコピーします。 *NSrc*が8ビット値の場合、このの VARTYPE は VT_UI1 に設定されます。 *NSrc*が16ビット値で、このの VARTYPE が VT_BOOL の場合、この値は保持されます。それ以外の場合は、VT_I2 に設定されます。

- **operator = (** *lsrc* **)** 32ビット整数値をこのオブジェクトにコピーします。 このの VARTYPE が VT_ERROR の場合は、保持されます。それ以外の場合は、VT_I4 に設定されます。

- **operator = (** *cursrc* **)** [COleCurrency](../../mfc/reference/colecurrency-class.md)オブジェクトをこのオブジェクトにコピーし、VARTYPE を VT_CY に設定します。

- **operator = (** *fltsrc* **)** 32ビットの浮動小数点値をこのオブジェクトにコピーし、VARTYPE を VT_R4 に設定します。

- **operator = (** *dblsrc* **)** 64ビットの浮動小数点値をこのオブジェクトにコピーし、VARTYPE を VT_R8 に設定します。

- **operator = (** ? *rc* **)** [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトをこのオブジェクトにコピーし、VARTYPE を VT_DATE に設定します。

- **operator = (** *arrsrc* **)** [CByteArray](../../mfc/reference/cbytearray-class.md)オブジェクトをこの`COleVariant`オブジェクトにコピーします。

- **operator = (** *lbSrc* **)** [CLongBinary](../../mfc/reference/clongbinary-class.md)オブジェクトをこの`COleVariant`オブジェクトにコピーします。

詳細については、Windows SDK の[バリアント](/windows/win32/api/oaidl/ns-oaidl-variant)と[varenum](/windows/win32/api/wtypes/ne-wtypes-varenum)のエントリを参照してください。

##  <a name="operator_eq_eq"></a>COleVariant:: operator = =

この演算子は、2つのバリアント型の値を比較し、等しい場合は0以外の値を返します。それ以外の場合は0です。

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

##  <a name="operator_lt_lt__gt_gt"></a>COleVariant:: operator &lt;、 &lt;&gt;&gt;

`CArchive` `COleVariant`値をまたは`CArchive` `CdumpContext`に出力し、からオブジェクトを入力します。 `COleVariant`

```
friend CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    OleVariant varSrc);

friend CArchive& AFXAPI operator<<(
    CArchive& ar,
    COleVariant varSrc);

friend CArchive& AFXAPI operator>>(
    CArchive& ar,
    COleVariant& varSrc);
```

### <a name="remarks"></a>Remarks

挿入`COleVariant` **(\<) 演算子は、診断ダンプをサポートし、アーカイブに保存します。\<** 抽出 ( **>>** ) 演算子は、アーカイブからの読み込みをサポートしています。

##  <a name="setstring"></a>COleVariant:: SetString

文字列を特定の型に設定します。

```
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>パラメーター

*lpszSrc*<br/>
新しい`COleVariant`オブジェクトにコピーされる null で終わる文字列。

*VtSrc*<br/>
新しい`COleVariant`オブジェクトの VARTYPE。

### <a name="remarks"></a>Remarks

*Vtsrc*のパラメーターには、VT_BSTR (UNICODE) または VT_BSTRT (ANSI) を指定する必要があります。 `SetString`は通常、文字列または文字列ポインターパラメーターを持つ[COleVariant:: COleVariant](#colevariant)コンストラクターの既定値で、VARTYPE が UNICODE ではないため、文字列を ANSI に設定するために使用されます。

UNICODE 以外のビルドの DAO レコードセットは、文字列が ANSI であることを想定しています。 したがって、dao の場合に使用する関数`COleVariant`UNICODE レコード セットを作成していない場合、オブジェクトが使用する必要があります、 **COleVariant::COleVariant (** *lpszSrc* **、** *vtSrc* **)** 形式を持つコンストラクターの*vtSrc* VT_BSTRT (ANSI) に設定または使用`SetString`で*vtSrc* VT に設定ANSI 文字列の作成に _BSTRT します。 たとえば、関数の`CDaoRecordset` [cdaorecordset:: Seek](../../mfc/reference/cdaorecordset-class.md#seek)と[cdaorecordset:: SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue)は、 `COleVariant`パラメーターとしてオブジェクトを使用します。 DAO レコードセットが UNICODE でない場合、これらのオブジェクトは ANSI である必要があります。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
