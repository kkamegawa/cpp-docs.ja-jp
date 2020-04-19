---
title: COleDispatchException クラス
ms.date: 11/04/2016
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
ms.openlocfilehash: 2d5b9d2a0dc1e716ea8cb20f0d0dcb4c5d765079
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341621"
---
# <a name="coledispatchexception-class"></a>COleDispatchException クラス

OLE オートメーションの主要部分である OLE `IDispatch` インターフェイス固有の例外を処理します。

## <a name="syntax"></a>構文

```
class COleDispatchException : public CException
```

## <a name="members"></a>メンバー

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|エラーのヘルプ コンテキスト。|
|[COleDispatchException::m_strDescription](#m_strdescription)|文章によるエラーの説明です。|
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|ヘルプ ファイルを使用する`m_dwHelpContext`します。|
|[COleDispatchException::m_strSource](#m_strsource)|例外を生成したアプリケーションです。|
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`-特定のエラー コード。|

## <a name="remarks"></a>Remarks

派生したその他の例外クラスと同様に、`CException`基本クラス、 `COleDispatchException` THROW、THROW_LAST、TRY、CATCH、AND_CATCH、および END_CATCH マクロで使用できます。

一般に、呼び出す必要がある[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)を作成し、スロー、`COleDispatchException`オブジェクト。

例外の詳細については、記事をご覧ください。[例外処理 (MFC)](../../mfc/exception-handling-in-mfc.md)と[例外。OLE の例外](../../mfc/exceptions-ole-exceptions.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleDispatchException`

## <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

##  <a name="m_dwhelpcontext"></a>  COleDispatchException::m_dwHelpContext

アプリケーションのヘルプのヘルプ コンテキストを識別する (します。HLP) ファイルです。

```
DWORD m_dwHelpContext;
```

### <a name="remarks"></a>Remarks

このメンバーは、関数によって設定[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)例外がスローされます。

### <a name="example"></a>例

  [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)の例を参照してください。

##  <a name="m_strdescription"></a>  COleDispatchException::m_strDescription

「ディスクがいっぱいです」など、口頭でのエラーの説明が含まれています

```
CString m_strDescription;
```

### <a name="remarks"></a>Remarks

このメンバーは、関数によって設定[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)例外がスローされます。

### <a name="example"></a>例

  [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)の例を参照してください。

##  <a name="m_strhelpfile"></a>  COleDispatchException::m_strHelpFile

フレームワークは、アプリケーションのヘルプ ファイルの名前では、この文字列に格納します。

```
CString m_strHelpFile;
```

##  <a name="m_strsource"></a>  COleDispatchException::m_strSource

フレームワークは、例外を生成したアプリケーションの名前では、この文字列に格納します。

```
CString m_strSource;
```

### <a name="example"></a>例

  [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)の例を参照してください。

##  <a name="m_wcode"></a>  COleDispatchException::m_wCode

アプリケーションに固有のエラー コードが含まれています。

```
WORD m_wCode;
```

### <a name="remarks"></a>Remarks

このメンバーは、関数によって設定[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)例外がスローされます。

## <a name="see-also"></a>関連項目

[MFC サンプル CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException クラス](../../mfc/reference/cexception-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleDispatchDriver クラス](../../mfc/reference/coledispatchdriver-class.md)<br/>
[COleException クラス](../../mfc/reference/coleexception-class.md)
