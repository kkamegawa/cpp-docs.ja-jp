---
title: COleException クラス
ms.date: 11/04/2016
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
ms.openlocfilehash: 96061f704d9df6cd788e362652b6ed22a7ffa999
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503946"
---
# <a name="coleexception-class"></a>COleException クラス

OLE 操作に関する例外条件を表します。

## <a name="syntax"></a>構文

```
class COleException : public CException
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleException::P rocess](#process)|キャッチされた例外を OLE のリターンコードに変換します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[COleException:: m_sc](#m_sc)|例外の理由を示すステータスコードを格納します。|

## <a name="remarks"></a>Remarks

クラス`COleException`には、例外の原因を示す状態コードを保持するパブリックデータメンバーが含まれています。

一般に、オブジェクトを`COleException`直接作成することは避けてください。代わりに、 [AfxThrowOleException](exception-processing.md#afxthrowoleexception)を呼び出す必要があります。

例外の詳細については、「[例外処理 (MFC)](../../mfc/exception-handling-in-mfc.md)と[例外」を参照してください。OLE の](../../mfc/exceptions-ole-exceptions.md)例外。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

##  <a name="m_sc"></a>COleException:: m_sc

このデータメンバーは、例外の原因を示す OLE ステータスコードを保持します。

```
SCODE m_sc;
```

### <a name="remarks"></a>Remarks

この変数の値は、 [AfxThrowOleException](exception-processing.md#afxthrowoleexception)によって設定されます。

SCODE の詳細については、「Windows SDK の[COM エラーコードの構造](/windows/win32/com/structure-of-com-error-codes)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

##  <a name="process"></a>  COleException::Process

キャッチされた例外を OLE ステータスコードに変換するには、**プロセス**メンバー関数を呼び出します。

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>パラメーター

*pAnyException*<br/>
キャッチされた例外へのポインター。

### <a name="return-value"></a>戻り値

OLE ステータスコード。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  この関数は**静的**です。

SCODE の詳細については、「Windows SDK の[COM エラーコードの構造](/windows/win32/com/structure-of-com-error-codes)」を参照してください。

### <a name="example"></a>例

  [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)の例を参照してください。

## <a name="see-also"></a>関連項目

[MFC のサンプル CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException クラス](../../mfc/reference/cexception-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
