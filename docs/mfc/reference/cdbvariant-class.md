---
title: CDBVariant クラス
ms.date: 11/04/2016
f1_keywords:
- CDBVariant
- AFXDB/CDBVariant
- AFXDB/CDBVariant::CDBVariant
- AFXDB/CDBVariant::Clear
- AFXDB/CDBVariant::m_dwType
- AFXDB/CDBVariant::m_boolVal
- AFXDB/CDBVariant::m_chVal
- AFXDB/CDBVariant::m_dblVal
- AFXDB/CDBVariant::m_fltVal
- AFXDB/CDBVariant::m_iVal
- AFXDB/CDBVariant::m_lVal
- AFXDB/CDBVariant::m_pbinary
- AFXDB/CDBVariant::m_pdate
- AFXDB/CDBVariant::m_pstring
- AFXDB/CDBVariant::m_pstringA
- AFXDB/CDBVariant::m_pstringW
helpviewer_keywords:
- CDBVariant [MFC], CDBVariant
- CDBVariant [MFC], Clear
- CDBVariant [MFC], m_dwType
- CDBVariant [MFC], m_boolVal
- CDBVariant [MFC], m_chVal
- CDBVariant [MFC], m_dblVal
- CDBVariant [MFC], m_fltVal
- CDBVariant [MFC], m_iVal
- CDBVariant [MFC], m_lVal
- CDBVariant [MFC], m_pbinary
- CDBVariant [MFC], m_pdate
- CDBVariant [MFC], m_pstring
- CDBVariant [MFC], m_pstringA
- CDBVariant [MFC], m_pstringW
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
ms.openlocfilehash: 48a2e08d056e3bfef8a06b80ae6607947923cbcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253323"
---
# <a name="cdbvariant-class"></a>CDBVariant クラス

MFC ODBC クラスのバリアント型を表します。

## <a name="syntax"></a>構文

```
class CDBVariant
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDBVariant::CDBVariant](#cdbvariant)|`CDBVariant` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDBVariant::Clear](#clear)|消去、`CDBVariant`オブジェクト。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CDBVariant::m_dwType](#m_dwtype)|現在格納されている値のデータ型が含まれています。 「`DWORD`」と入力します。|

### <a name="public-union-members"></a>パブリックの共用体のメンバー

|名前|説明|
|----------|-----------------|
|[CDBVariant::m_boolVal](#m_boolval)|型の値を含む**BOOL**します。|
|[CDBVariant::m_chVal](#m_chval)|型の値を含む**unsigned char**します。|
|[CDBVariant::m_dblVal](#m_dblval)|型の値を含む**double**します。|
|[CDBVariant::m_fltVal](#m_fltval)|型の値を含む**float**します。|
|[CDBVariant::m_iVal](#m_ival)|型の値を含む**short**します。|
|[CDBVariant::m_lVal](#m_lval)|型の値を含む**long**します。|
|[CDBVariant::m_pbinary](#m_pbinary)|型のオブジェクトへのポインターを含む`CLongBinary`します。|
|[CDBVariant::m_pdate](#m_pdate)|型のオブジェクトへのポインターを含む**TIMESTAMP_STRUCT**します。|
|[CDBVariant::m_pstring](#m_pstring)|型のオブジェクトへのポインターを含む`CString`します。|
|[CDBVariant::m_pstringA](#m_pstringa)|ASCII へのポインターを格納[CString](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクト。|
|[CDBVariant::m_pstringW](#m_pstringw)|幅広いへのポインターを格納[CString](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクト。|

## <a name="remarks"></a>Remarks

`CDBVariant` 基本クラスはありません。

`CDBVariant` ような[COleVariant](../../mfc/reference/colevariant-class.md)。 ただし、 `CDBVariant` OLE は使用しません。 `CDBVariant` 値のデータ型について悩むことがなく値を格納することができます。 `CDBVariant` 共用体に格納されている現在の値のデータ型を追跡します。

クラス[CRecordset](../../mfc/reference/crecordset-class.md)利用`CDBVariant`3 つのメンバー関数内のオブジェクト: `GetFieldValue`、 `GetBookmark`、および`SetBookmark`します。 たとえば、`GetFieldValue`列のデータを動的にフェッチすることができます。 実行時に、列のデータ型を認識しない可能性があるため`GetFieldValue`を使用して、`CDBVariant`列のデータを格納するオブジェクト。

## <a name="inheritance-hierarchy"></a>継承階層

`CDBVariant`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdb.h

##  <a name="cdbvariant"></a>  CDBVariant::CDBVariant

Null 値を作成します。`CDBVariant`オブジェクト。

```
CDBVariant();
```

### <a name="remarks"></a>Remarks

セット、 [m_dwType](#m_dwtype) DBVT_NULL するデータ メンバー。

##  <a name="clear"></a>  CDBVariant::Clear

クリアするには、このメンバー関数を呼び出す、`CDBVariant`オブジェクト。

```
void Clear();
```

### <a name="remarks"></a>Remarks

場合の値、 [m_dwType](#m_dwtype)データ メンバーは DBVT_DATE、DBVT_STRING、または DBVT_BINARY、`Clear`共用体ポインター メンバーに関連付けられているメモリを解放します。 `Clear` 設定`m_dwType`DBVT_NULL にします。

`CDBVariant`デストラクター呼び出し`Clear`します。

##  <a name="m_boolval"></a>  CDBVariant::m_boolVal

BOOL 型の値を格納します。

### <a name="remarks"></a>Remarks

`m_boolVal`共用体へのデータ メンバーが属しています。 アクセスする前に`m_boolVal`、最初の値をチェック[CDBVariant::m_dwType](#m_dwtype)します。 場合`m_dwType`DBVT_BOOL に設定し、`m_boolVal`有効な値が含まれます。 それ以外の場合、にアクセスする`m_boolVal`信頼性のない結果が生成されます。

##  <a name="m_chval"></a>  CDBVariant::m_chVal

型の値を格納**unsigned char**します。

### <a name="remarks"></a>Remarks

`m_chVal`共用体へのデータ メンバーが属しています。 アクセスする前に`m_chVal`、最初の値をチェック[CDBVariant::m_dwType](#m_dwtype)します。 場合`m_dwType`DBVT_UCHAR に設定し、`m_chVal`有効な値が含まれています。 それ以外の場合、にアクセスする`m_chVal`信頼性のない結果が生成されます。

##  <a name="m_dblval"></a>  CDBVariant::m_dblVal

型の値を格納**double**します。

### <a name="remarks"></a>Remarks

`m_dblVal`共用体へのデータ メンバーが属しています。 アクセスする前に`m_dblVal`、最初の値をチェック[CDBVariant::m_dwType](#m_dwtype)します。 場合`m_dwType`DBVT_DOUBLE に設定し、`m_dblVal`有効な値が含まれています。 それ以外の場合、にアクセスする`m_dblVal`信頼性のない結果が生成されます。

##  <a name="m_dwtype"></a>  CDBVariant::m_dwType

このデータ メンバーに現在格納されている値のデータ型が含まれています、`CDBVariant`オブジェクトの共用体データ メンバー。

### <a name="remarks"></a>Remarks

この共用体にアクセスする前に、の値を確認する必要があります`m_dwType`にアクセスするには、どの共用体データ メンバーを決定するためにします。 次の表に、可能な値`m_dwType`と対応する共用体データ メンバー。

|m_dwType|共用体データ メンバー|
|---------------|-----------------------|
|DBVT_NULL|共用体のメンバーがアクセスに対して有効ではありません。|
|DBVT_BOOL|[m_boolVal](#m_boolval)|
|DBVT_UCHAR|[m_chVal](#m_chval)|
|DBVT_SHORT|[m_iVal](#m_ival)|
|DBVT_LONG|[m_lVal](#m_lval)|
|DBVT_SINGLE|[m_fltVal](#m_fltval)|
|DBVT_DOUBLE|[m_dblVal](#m_dblval)|
|DBVT_DATE|[m_pdate](#m_pdate)|
|DBVT_STRING|[m_pstring](#m_pstring)|
|DBVT_BINARY|[m_pbinary](#m_pbinary)|
|DBVT_ASTRING|[m_pstringA](#m_pstringa)|
|DBVT_WSTRING|[m_pstringW](#m_pstringw)|

##  <a name="m_fltval"></a>  CDBVariant::m_fltVal

型の値を格納**float**します。

### <a name="remarks"></a>Remarks

`m_fltVal`共用体へのデータ メンバーが属しています。 アクセスする前に`m_fltVal`、最初の値をチェック[CDBVariant::m_dwType](#m_dwtype)します。 場合`m_dwType`DBVT_SINGLE に設定し、`m_fltVal`有効な値が含まれています。 それ以外の場合、にアクセスする`m_fltVal`信頼性のない結果が生成されます。

##  <a name="m_ival"></a>  CDBVariant::m_iVal

型の値を格納**short**します。

### <a name="remarks"></a>Remarks

`m_iVal`共用体へのデータ メンバーが属しています。 アクセスする前に`m_iVal`、最初の値をチェック[CDBVariant::m_dwType](#m_dwtype)します。 場合`m_dwType`DBVT_SHORT に設定し、`m_iVal`有効な値が含まれています。 それ以外の場合、にアクセスする`m_iVal`信頼性のない結果が生成されます。

##  <a name="m_lval"></a>  CDBVariant::m_lVal

型の値を格納**long**します。

### <a name="remarks"></a>Remarks

`m_lVal`共用体へのデータ メンバーが属しています。 アクセスする前に`m_lVal`、最初の値をチェック[CDBVariant::m_dwType](#m_dwtype)します。 場合`m_dwType`DBVT_LONG に設定し、`m_lVal`有効な値が含まれています。 それ以外の場合、にアクセスする`m_lVal`信頼性のない結果が生成されます。

##  <a name="m_pbinary"></a>  CDBVariant::m_pbinary

型のオブジェクトへのポインターを格納[CLongBinary](../../mfc/reference/clongbinary-class.md)します。

### <a name="remarks"></a>Remarks

`m_pbinary`共用体へのデータ メンバーが属しています。 アクセスする前に`m_pbinary`、最初の値をチェック[CDBVariant::m_dwType](#m_dwtype)します。 場合`m_dwType`DBVT_BINARY に設定し、`m_pbinary`の有効なポインターが含まれています。 それ以外の場合、にアクセスする`m_pbinary`信頼性のない結果が生成されます。

##  <a name="m_pdate"></a>  CDBVariant::m_pdate

TIMESTAMP_STRUCT 型のオブジェクトへのポインターを格納します。

### <a name="remarks"></a>Remarks

`m_pdate`共用体へのデータ メンバーが属しています。 アクセスする前に`m_pdate`、最初の値をチェック[CDBVariant::m_dwType](#m_dwtype)します。 場合`m_dwType`DBVT_DATE に設定し、`m_pdate`の有効なポインターが含まれています。 それ以外の場合、にアクセスする`m_pdate`信頼性のない結果が生成されます。

TIMESTAMP_STRUCT のデータ型の詳細については、トピックを参照してください。 [C データ型](/sql/odbc/reference/appendixes/c-data-types)の付録 d、 *ODBC プログラマ リファレンス*Windows SDK にします。

##  <a name="m_pstring"></a>  CDBVariant::m_pstring

型のオブジェクトへのポインターを格納[CString](../../atl-mfc-shared/reference/cstringt-class.md)します。

### <a name="remarks"></a>Remarks

`m_pstring`共用体へのデータ メンバーが属しています。 アクセスする前に`m_pstring`、最初の値をチェック[CDBVariant::m_dwType](#m_dwtype)します。 場合`m_dwType`DBVT_STRING に設定し、`m_pstring`の有効なポインターが含まれています。 それ以外の場合、にアクセスする`m_pstring`信頼性のない結果が生成されます。

##  <a name="m_pstringa"></a>  CDBVariant::m_pstringA

ASCII へのポインターを格納[CString](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクト。

### <a name="remarks"></a>Remarks

`m_pstringA`共用体へのデータ メンバーが属しています。 アクセスする前に`m_pstringA`、最初の値をチェック[CDBVariant::m_dwType](#m_dwtype)します。 場合`m_dwType`DBVT_ASTRING に設定し、`m_pstringA`の有効なポインターが含まれています。 それ以外の場合、にアクセスする`m_pstringA`信頼性のない結果が生成されます。

##  <a name="m_pstringw"></a>  CDBVariant::m_pstringW

幅広いへのポインターを格納[CString](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクト。

### <a name="remarks"></a>Remarks

`m_pstringW`共用体へのデータ メンバーが属しています。 アクセスする前に`m_pstringW`、最初の値をチェック[CDBVariant::m_dwType](#m_dwtype)します。 場合`m_dwType`DBVT_WSTRING に設定し、`m_pstringW`の有効なポインターが含まれています。 それ以外の場合、にアクセスする`m_pstringW`信頼性のない結果が生成されます。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)
