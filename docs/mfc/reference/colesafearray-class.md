---
title: COleSafeArray クラス
ms.date: 08/29/2019
f1_keywords:
- COleSafeArray
- AFXDISP/COleSafeArray
- AFXDISP/COleSafeArray::COleSafeArray
- AFXDISP/COleSafeArray::AccessData
- AFXDISP/COleSafeArray::AllocData
- AFXDISP/COleSafeArray::AllocDescriptor
- AFXDISP/COleSafeArray::Attach
- AFXDISP/COleSafeArray::Clear
- AFXDISP/COleSafeArray::Copy
- AFXDISP/COleSafeArray::Create
- AFXDISP/COleSafeArray::CreateOneDim
- AFXDISP/COleSafeArray::Destroy
- AFXDISP/COleSafeArray::DestroyData
- AFXDISP/COleSafeArray::DestroyDescriptor
- AFXDISP/COleSafeArray::Detach
- AFXDISP/COleSafeArray::GetByteArray
- AFXDISP/COleSafeArray::GetDim
- AFXDISP/COleSafeArray::GetElement
- AFXDISP/COleSafeArray::GetElemSize
- AFXDISP/COleSafeArray::GetLBound
- AFXDISP/COleSafeArray::GetOneDimSize
- AFXDISP/COleSafeArray::GetUBound
- AFXDISP/COleSafeArray::Lock
- AFXDISP/COleSafeArray::PtrOfIndex
- AFXDISP/COleSafeArray::PutElement
- AFXDISP/COleSafeArray::Redim
- AFXDISP/COleSafeArray::ResizeOneDim
- AFXDISP/COleSafeArray::UnaccessData
- AFXDISP/COleSafeArray::Unlock
helpviewer_keywords:
- COleSafeArray [MFC], COleSafeArray
- COleSafeArray [MFC], AccessData
- COleSafeArray [MFC], AllocData
- COleSafeArray [MFC], AllocDescriptor
- COleSafeArray [MFC], Attach
- COleSafeArray [MFC], Clear
- COleSafeArray [MFC], Copy
- COleSafeArray [MFC], Create
- COleSafeArray [MFC], CreateOneDim
- COleSafeArray [MFC], Destroy
- COleSafeArray [MFC], DestroyData
- COleSafeArray [MFC], DestroyDescriptor
- COleSafeArray [MFC], Detach
- COleSafeArray [MFC], GetByteArray
- COleSafeArray [MFC], GetDim
- COleSafeArray [MFC], GetElement
- COleSafeArray [MFC], GetElemSize
- COleSafeArray [MFC], GetLBound
- COleSafeArray [MFC], GetOneDimSize
- COleSafeArray [MFC], GetUBound
- COleSafeArray [MFC], Lock
- COleSafeArray [MFC], PtrOfIndex
- COleSafeArray [MFC], PutElement
- COleSafeArray [MFC], Redim
- COleSafeArray [MFC], ResizeOneDim
- COleSafeArray [MFC], UnaccessData
- COleSafeArray [MFC], Unlock
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
ms.openlocfilehash: a0ce0fc03923806c9e044a7edae3178fd3429b76
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177401"
---
# <a name="colesafearray-class"></a>COleSafeArray クラス

任意の型および次元の配列を扱うクラスです。

## <a name="syntax"></a>構文

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleSafeArray:: COleSafeArray](#colesafearray)|`COleSafeArray` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleSafeArray:: AccessData](#accessdata)|配列データへのポインターを取得します。|
|[COleSafeArray:: AllocData](#allocdata)|配列にメモリを割り当てます。|
|[COleSafeArray:: AllocDescriptor](#allocdescriptor)|セーフ配列記述子にメモリを割り当てます。|
|[COleSafeArray:: Attach](#attach)|オブジェクトに対する既存`VARIANT`の配列の制御を提供します。 `COleSafeArray`|
|[COleSafeArray:: Clear](#clear)|基になる`VARIANT`のすべてのデータを解放します。|
|[COleSafeArray:: Copy](#copy)|既存の配列のコピーを作成します。|
|[COleSafeArray:: Create](#create)|セーフ配列を作成します。|
|[COleSafeArray:: CreateOneDim](#createonedim)|1次元`COleSafeArray`のオブジェクトを作成します。|
|[COleSafeArray::D estroy](#destroy)|既存の配列を破棄します。|
|[COleSafeArray::D estroyData](#destroydata)|安全な配列のデータを破棄します。|
|[COleSafeArray::D estroyDescriptor](#destroydescriptor)|セーフ配列の記述子を破棄します。|
|[COleSafeArray::D etach](#detach)|`COleSafeArray`オブジェクトから VARIANT 配列をデタッチします (データが解放されないようにするため)。|
|[COleSafeArray:: GetByteArray](#getbytearray)|セーフ配列の内容を[CByteArray](../../mfc/reference/cbytearray-class.md)にコピーします。|
|[COleSafeArray:: GetDim](#getdim)|配列内の次元数を返します。|
|[COleSafeArray:: GetElement](#getelement)|セーフ配列の1つの要素を取得します。|
|[COleSafeArray:: GetElemSize](#getelemsize)|セーフ配列内の1つの要素のサイズ (バイト単位) を返します。|
|[COleSafeArray:: GetLBound](#getlbound)|セーフ配列の任意の次元の下限を返します。|
|[COleSafeArray:: GetOneDimSize](#getonedimsize)|1次元`COleSafeArray`のオブジェクト内の要素の数を返します。|
|[COleSafeArray:: GetUBound](#getubound)|セーフ配列の任意の次元の上限を返します。|
|[COleSafeArray:: Lock](#lock)|配列のロックカウントをインクリメントし、配列データへのポインターを配列記述子に配置します。|
|[COleSafeArray::P trOfIndex](#ptrofindex)|インデックス付き要素へのポインターを返します。|
|[COleSafeArray::P utElement](#putelement)|1 つの要素を配列に割り当てます。|
|[COleSafeArray::Redim](#redim)|セーフ配列の最上位 (右端) の下限を変更します。|
|[COleSafeArray:: ResizeOneDim](#resizeonedim)|1次元`COleSafeArray`のオブジェクト内の要素の数を変更します。|
|[COleSafeArray:: UnaccessData](#unaccessdata)|配列のロックカウントをデクリメントし、によって`AccessData`取得されたポインターを無効にします。|
|[COleSafeArray:: Unlock](#unlock)|配列のロックカウントをデクリメントして、解放またはサイズ変更できるようにします。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[COleSafeArray:: operator LPCVARIANT](#operator_lpcvariant)|オブジェクトの基`VARIANT`になる構造にアクセスします。 `COleSafeArray`|
|[COleSafeArray:: operator LPVARIANT](#operator_lpvariant)|オブジェクトの基`VARIANT`になる構造にアクセスします。 `COleSafeArray`|
|[COleSafeArray:: operator =](#operator_eq)|`COleSafeArray`値を`COleSafeArray`オブジェクト (`SAFEARRAY` `VARIANT` 、`COleVariant`、、または配列) にコピーします。|
|[COleSafeArray:: operator = =](#operator_eq_eq)|`SAFEARRAY`2 つ`VARIANT`のvariant配列(`COleSafeArray` 、、 、または配列)を比較します。`COleVariant`|
|[COleSafeArray:: operator&lt;&lt;](#operator_lt_lt)|`COleSafeArray`オブジェクトの内容をダンプコンテキストに出力します。|

## <a name="remarks"></a>Remarks

`COleSafeArray`OLE `VARIANT`構造体から派生します。 OLE `SAFEARRAY`メンバー関数は、を介し`COleSafeArray`て使用できます。また、1次元のバイト配列専用に設計された一連のメンバー関数も使用できます。

## <a name="inheritance-hierarchy"></a>継承階層

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

##  <a name="accessdata"></a>COleSafeArray:: AccessData

配列データへのポインターを取得します。

```
void AccessData(void** ppvData);
```

### <a name="parameters"></a>パラメーター

*ppvData*<br/>
配列データへのポインターへのポインター。

### <a name="remarks"></a>Remarks

エラーが発生した場合、関数は[CMemoryException](../../mfc/reference/cmemoryexception-class.md)または[COleException](../../mfc/reference/coleexception-class.md)をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

##  <a name="allocdata"></a>  COleSafeArray::AllocData

セーフ配列にメモリを割り当てます。

```
void AllocData();
```

### <a name="remarks"></a>Remarks

エラーが発生した場合、関数は[CMemoryException](../../mfc/reference/cmemoryexception-class.md)または[COleException](../../mfc/reference/coleexception-class.md)をスローします。

##  <a name="allocdescriptor"></a>COleSafeArray:: AllocDescriptor

セーフ配列の記述子にメモリを割り当てます。

```
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>パラメーター

*dwDims*<br/>
セーフ配列内の次元の数。

### <a name="remarks"></a>Remarks

エラーが発生した場合、関数は[CMemoryException](../../mfc/reference/cmemoryexception-class.md)または[COleException](../../mfc/reference/coleexception-class.md)をスローします。

##  <a name="attach"></a>COleSafeArray:: Attach

既存`VARIANT`の配列内のデータの制御`COleSafeArray`をオブジェクトに提供します。

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>パラメーター

*varSrc*<br/>
`VARIANT` オブジェクト。 *Varsrc*パラメーターには、VARTYPE [VT_ARRAY](/windows/win32/api/wtypes/ne-wtypes-varenum)を指定する必要があります。

### <a name="remarks"></a>Remarks

ソース`VARIANT`の種類が VT_EMPTY に設定されています。 この関数は、現在の配列データ (存在する場合) をクリアします。

### <a name="example"></a>例

  [COleSafeArray:: AccessData](#accessdata)の例を参照してください。

##  <a name="clear"></a>COleSafeArray:: Clear

セーフ配列をクリアします。

```
void Clear();
```

### <a name="remarks"></a>Remarks

関数は、オブジェクト`VARTYPE`のを VT_EMPTY に設定することによって、セーフ配列をクリアします。 現在の内容が解放され、配列が解放されます。

##  <a name="colesafearray"></a>COleSafeArray:: COleSafeArray

`COleSafeArray` オブジェクトを構築します。

```
COleSafeArray();

COleSafeArray(
    const SAFEARRAY& saSrc,
    VARTYPE vtSrc);

COleSafeArray(
    LPCSAFEARRAY pSrc,
    VARTYPE vtSrc);

COleSafeArray(const COleSafeArray& saSrc);
COleSafeArray(const VARIANT& varSrc);
COleSafeArray(LPCVARIANT pSrc);
COleSafeArray(const COleVariant& varSrc);
```

### <a name="parameters"></a>パラメーター

*saSrc*<br/>
新しい`SAFEARRAY` `COleSafeArray` オブジェクトにコピーされる既存の`COleSafeArray`オブジェクトまたは。

*vtSrc*<br/>
新しい`COleSafeArray`オブジェクトの VARTYPE。

*psaSrc*<br/>
`SAFEARRAY` 新しい`COleSafeArray`オブジェクトにコピーされるへのポインター。

*varSrc*<br/>
新しい`COleVariant` `VARIANT` オブジェクトにコピーされる既存の`COleSafeArray`またはオブジェクト。

*.Psrc*<br/>
`VARIANT` 新しい`COleSafeArray`オブジェクトにコピーされるオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

これらのコンストラクターはすべて、 `COleSafeArray`新しいオブジェクトを作成します。 パラメーターがない場合は、空`COleSafeArray`のオブジェクトが作成されます (VT_EMPTY)。 が暗黙的に認識されている別の配列`COleSafeArray`(、 `COleVariant`、または`VARIANT`) からがコピーされた場合、ソース配列のvartypeは保持されるため、指定する必要はありません。`COleSafeArray` が認識されていない別の配列 (`SAFEARRAY`) からコピーされた場合は、vtsrcパラメーターでvartypeを指定する必要があります。`COleSafeArray`

エラーが発生した場合、関数は[CMemoryException](../../mfc/reference/cmemoryexception-class.md)または[COleException](../../mfc/reference/coleexception-class.md)をスローします。

##  <a name="copy"></a>COleSafeArray:: Copy

既存のセーフ配列のコピーを作成します。

```
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>パラメーター

*ppsa*<br/>
新しい配列記述子を返す位置へのポインター。

### <a name="remarks"></a>Remarks

エラーが発生した場合、関数は[CMemoryException](../../mfc/reference/cmemoryexception-class.md)または[COleException](../../mfc/reference/coleexception-class.md)をスローします。

##  <a name="create"></a>COleSafeArray:: Create

配列のデータを割り当てて初期化します。

```
void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    DWORD* rgElements);

void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    SAFEARRAYBOUND* rgsabounds);
```

### <a name="parameters"></a>パラメーター

*vtSrc*<br/>
配列の基本型 (つまり、配列の各要素の VARTYPE)。 VARTYPE は、バリアント型のサブセットに制限されます。 VT_ARRAY と VT_BYREF の両方のフラグを設定することはできません。 VT_EMPTY と VT_NULL は、配列の有効な基本型ではありません。 それ以外の型はすべて有効です。

*dwDims*<br/>
配列内の次元の数。 これは、 [Redim](#redim)で配列を作成した後に変更できます。

*rgElements*<br/>
配列内の各次元の要素数の配列へのポインター。

*rgsabounds*<br/>
配列に割り当てる境界のベクター (次元ごとに1つ) へのポインター。

### <a name="remarks"></a>Remarks

この関数は、必要に応じて現在の配列データをクリアします。 エラーが発生した場合、関数は[CMemoryException](../../mfc/reference/cmemoryexception-class.md)をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="createonedim"></a>COleSafeArray:: CreateOneDim

新しい1次元`COleSafeArray`オブジェクトを作成します。

```
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>パラメーター

*vtSrc*<br/>
配列の基本型 (つまり、配列の各要素の VARTYPE)。

*dwElements*<br/>
配列内の要素の数。 これは、 [ResizeOneDim](#resizeonedim)を使用して配列を作成した後に変更できます。

*pvSrcData*<br/>
配列にコピーするデータへのポインター。

*nLBound*<br/>
配列の下限。

### <a name="remarks"></a>Remarks

関数は、配列のデータを割り当てて初期化し、ポインターの*Pvsrcdata*が NULL でない場合に、指定されたデータをコピーします。

エラーが発生した場合、関数は[CMemoryException](../../mfc/reference/cmemoryexception-class.md)をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

##  <a name="destroy"></a>COleSafeArray::D estroy

既存の配列記述子と配列内のすべてのデータを破棄します。

```
void Destroy();
```

### <a name="remarks"></a>Remarks

オブジェクトが配列に格納されている場合は、各オブジェクトが解放されます。 エラーが発生した場合、関数は[CMemoryException](../../mfc/reference/cmemoryexception-class.md)または[COleException](../../mfc/reference/coleexception-class.md)をスローします。

##  <a name="destroydata"></a>COleSafeArray::D estroyData

セーフ配列内のすべてのデータを破棄します。

```
void DestroyData();
```

### <a name="remarks"></a>Remarks

オブジェクトが配列に格納されている場合は、各オブジェクトが解放されます。 エラーが発生した場合、関数は[CMemoryException](../../mfc/reference/cmemoryexception-class.md)または[COleException](../../mfc/reference/coleexception-class.md)をスローします。

##  <a name="destroydescriptor"></a>COleSafeArray::D estroyDescriptor

セーフ配列の記述子を破棄します。

```
void DestroyDescriptor();
```

### <a name="remarks"></a>Remarks

エラーが発生した場合、関数は[CMemoryException](../../mfc/reference/cmemoryexception-class.md)または[COleException](../../mfc/reference/coleexception-class.md)をスローします。

##  <a name="detach"></a>COleSafeArray::D etach

オブジェクトからデータを`VARIANT`デタッチします。 `COleSafeArray`

```
VARIANT Detach();
```

### <a name="return-value"></a>戻り値

`COleSafeArray`オブジェクトの`VARIANT`基になる値。

### <a name="remarks"></a>Remarks

関数は、オブジェクトの VARTYPE を VT_EMPTY に設定することによって、データをセーフ配列にデタッチします。 Windows 関数[VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear)を呼び出すことによって、配列を解放するのは呼び出し元の責任です。

エラーが発生した場合、関数は[COleException](../../mfc/reference/coleexception-class.md)をスローします。

### <a name="example"></a>例

  [COleSafeArray::P utElement](#putelement)の例を参照してください。

##  <a name="getbytearray"></a>COleSafeArray:: GetByteArray

セーフ配列`CByteArray`の内容をにコピーします。

```
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>パラメーター

*メモリ*<br/>
[CByteArray](../../mfc/reference/cbytearray-class.md)オブジェクトへの参照。

##  <a name="getdim"></a>COleSafeArray:: GetDim

`COleSafeArray`オブジェクトの次元数を返します。

```
DWORD GetDim();
```

### <a name="return-value"></a>戻り値

セーフ配列内の次元の数。

### <a name="example"></a>例

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

##  <a name="getelement"></a>COleSafeArray:: GetElement

セーフ配列の1つの要素を取得します。

```
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>パラメーター

*rgIndices*<br/>
インデックスの配列へのポインター (配列の次元ごと)。

*pvData*<br/>
配列の要素を配置する位置へのポインター。

### <a name="remarks"></a>Remarks

この関数は、要素を取得`SafeArrayLock`する`SafeArrayUnlock`前と後に、windows の関数を自動的に呼び出します。 データ要素が文字列、オブジェクト、またはバリアントの場合、関数は正しい方法で要素をコピーします。 パラメーター *Pvdata*は、要素を格納するのに十分な大きさのバッファーを指している必要があります。

エラーが発生した場合、関数は[CMemoryException](../../mfc/reference/cmemoryexception-class.md)または[COleException](../../mfc/reference/coleexception-class.md)をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

##  <a name="getelemsize"></a>COleSafeArray:: GetElemSize

`COleSafeArray`オブジェクト内の要素のサイズを取得します。

```
DWORD GetElemSize();
```

### <a name="return-value"></a>戻り値

セーフ配列の要素のサイズ (バイト単位)。

##  <a name="getlbound"></a>COleSafeArray:: GetLBound

`COleSafeArray`オブジェクトの任意の次元の下限を返します。

```
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>パラメーター

*dwDim*<br/>
下限を取得する対象の配列の次元。

*pLBound*<br/>
下限を返す位置へのポインター。

### <a name="remarks"></a>Remarks

エラーが発生した場合、関数は[COleException](../../mfc/reference/coleexception-class.md)をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

##  <a name="getonedimsize"></a>COleSafeArray:: GetOneDimSize

1次元`COleSafeArray`のオブジェクト内の要素の数を返します。

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>戻り値

1次元のセーフ配列内の要素の数。

### <a name="example"></a>例

  [COleSafeArray:: CreateOneDim](#createonedim)の例を参照してください。

##  <a name="getubound"></a>COleSafeArray:: GetUBound

セーフ配列の任意の次元の上限を返します。

```
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>パラメーター

*dwDim*<br/>
上限を取得する対象の配列の次元。

*pUBound*<br/>
上限を返す位置へのポインター。

### <a name="remarks"></a>Remarks

エラーが発生した場合、関数は[COleException](../../mfc/reference/coleexception-class.md)をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

##  <a name="lock"></a>COleSafeArray:: Lock

配列のロックカウントをインクリメントし、配列データへのポインターを配列記述子に配置します。

```
void Lock();
```

### <a name="remarks"></a>Remarks

エラーが発生した場合、 [COleException](../../mfc/reference/coleexception-class.md)をスローします。

配列記述子内のポインターは、が呼び出さ`Unlock`れるまで有効です。 の呼び出しは入れ子にする`Unlock` ことができます。の呼び出しの数は同じである必要があります。`Lock`

配列はロックされている間は削除できません。

##  <a name="operator_lpcvariant"></a>COleSafeArray:: operator LPCVARIANT

このキャスト演算子を呼び出して、この`VARIANT` `COleSafeArray`オブジェクトの基になる構造体にアクセスします。

```
operator LPCVARIANT() const;
```

##  <a name="operator_lpvariant"></a>COleSafeArray:: operator LPVARIANT

このキャスト演算子を呼び出して、この`VARIANT` `COleSafeArray`オブジェクトの基になる構造体にアクセスします。

```
operator LPVARIANT();
```

### <a name="remarks"></a>Remarks

この関数によって返される`VARIANT`ポインターによってアクセスされる構造体の値を変更すると`COleSafeArray` 、このオブジェクトの値が変更されることに注意してください。

##  <a name="operator_eq"></a>COleSafeArray:: operator =

これらのオーバーロードされた代入演算子は、 `COleSafeArray` source 値をこのオブジェクトにコピーします。

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>Remarks

各演算子の簡単な説明を次に示します。

- **operator = (** *saSrc* **)** 既存`COleSafeArray`のオブジェクトをこのオブジェクトにコピーします。

- **operator = (** *varsrc* **)** 既存`VARIANT`のまたは`COleVariant`配列をこのオブジェクトにコピーします。

- **operator = (** *psrc* **)** `VARIANT` *Psrc*によってアクセスされる配列オブジェクトをこのオブジェクトにコピーします。

##  <a name="operator_eq_eq"></a>COleSafeArray:: operator = =

この`SAFEARRAY`演算子は`VARIANT` 、2つの`COleSafeArray`配列 (、、 、または配列)を比較し、等しい場合は0以外の値を返します。それ以外の場合は0を返します。`COleVariant`

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>Remarks

2つの配列は、次元数が等しい場合、各次元のサイズが等しい場合、および要素値が等しい場合に等しくなります。

##  <a name="operator_lt_lt"></a>COleSafeArray:: operator&lt;&lt;

挿入`COleSafeArray` (< <) 操作では、 `COleSafeArray`オブジェクトの診断ダンプとアーカイブへの格納がサポートされています。

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

##  <a name="ptrofindex"></a>COleSafeArray::P trOfIndex

インデックス値によって指定された要素へのポインターを返します。

```
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>パラメーター

*rgIndices*<br/>
配列の要素を識別するインデックス値の配列。 要素のすべてのインデックスを指定する必要があります。

*ppvData*<br/>
返されるときに、 *rgIndices*内の値によって識別される要素へのポインター。

##  <a name="putelement"></a>COleSafeArray::P utElement

1 つの要素を配列に割り当てます。

```
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>パラメーター

*rgIndices*<br/>
インデックスの配列へのポインター (配列の次元ごと)。

*pvData*<br/>
配列に割り当てるデータへのポインター。 VT_DISPATCH、VT_UNKNOWN、および VT_BSTR variant 型はポインターであり、別のレベルの間接参照を必要としません。

### <a name="remarks"></a>Remarks

この関数は、要素を割り当てる前と後に、Windows 関数[SafeArrayLock](/windows/win32/api/oleauto/nf-oleauto-safearraylock)と[SafeArrayUnlock](/windows/win32/api/oleauto/nf-oleauto-safearrayunlock)を自動的に呼び出します。 データ要素が文字列、オブジェクト、バリアントの場合は、関数によって適切にコピーされ、既存の要素が文字列、オブジェクト、バリアントの場合は、関数によって適切にクリアされます。

配列は多重にロックできるため、配列が別の操作によってロックされている間に要素を配列に配置できることに注意してください。

エラーが発生した場合、関数は[CMemoryException](../../mfc/reference/cmemoryexception-class.md)または[COleException](../../mfc/reference/coleexception-class.md)をスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

##  <a name="redim"></a>  COleSafeArray::Redim

セーフ配列の最上位 (右端) の下限を変更します。

```
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>パラメーター

*psaboundNew*<br/>
新しい配列のバインドを含む新しいセーフ配列のバインドされた構造体へのポインター。 配列の最下位次元のみが変更される可能性があります。

### <a name="remarks"></a>Remarks

エラーが発生した場合、関数は[COleException](../../mfc/reference/coleexception-class.md)をスローします。

##  <a name="resizeonedim"></a>COleSafeArray:: ResizeOneDim

1次元`COleSafeArray`のオブジェクト内の要素の数を変更します。

```
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>パラメーター

*dwElements*<br/>
1次元セーフ配列内の要素の数。

### <a name="remarks"></a>Remarks

エラーが発生した場合、関数は[COleException](../../mfc/reference/coleexception-class.md)をスローします。

### <a name="example"></a>例

  [COleSafeArray:: CreateOneDim](#createonedim)の例を参照してください。

##  <a name="unaccessdata"></a>COleSafeArray:: UnaccessData

配列のロックカウントをデクリメントし、によって`AccessData`取得されたポインターを無効にします。

```
void UnaccessData();
```

### <a name="remarks"></a>Remarks

エラーが発生した場合、関数は[COleException](../../mfc/reference/coleexception-class.md)をスローします。

### <a name="example"></a>例

  [COleSafeArray:: AccessData](#accessdata)の例を参照してください。

##  <a name="unlock"></a>COleSafeArray:: Unlock

配列のロックカウントをデクリメントして、解放またはサイズ変更できるようにします。

```
void Unlock();
```

### <a name="remarks"></a>Remarks

この関数は、配列内のデータへのアクセスが終了した後に呼び出されます。 エラーが発生した場合、 [COleException](../../mfc/reference/coleexception-class.md)をスローします。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleVariant クラス](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase クラス](../../mfc/reference/cdatabase-class.md)<br/>
