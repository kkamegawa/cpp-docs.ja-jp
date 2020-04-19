---
title: CInternetException クラス
ms.date: 11/04/2016
f1_keywords:
- CInternetException
- AFXINET/CInternetException
- AFXINET/CInternetException::CInternetException
- AFXINET/CInternetException::m_dwContext
- AFXINET/CInternetException::m_dwError
helpviewer_keywords:
- CInternetException [MFC], CInternetException
- CInternetException [MFC], m_dwContext
- CInternetException [MFC], m_dwError
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
ms.openlocfilehash: c4f4c7a5b7594270aff9dfbc224e9a66ba09be3f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505907"
---
# <a name="cinternetexception-class"></a>CInternetException クラス

インターネット操作に関する例外条件を表します。

## <a name="syntax"></a>構文

```
class CInternetException : public CException
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CInternetException:: CInternetException](#cinternetexception)|`CInternetException` オブジェクトを構築します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CInternetException:: m_dwContext](#m_dwcontext)|例外の原因となった操作に関連付けられたコンテキスト値。|
|[CInternetException:: m_dwError](#m_dwerror)|例外の原因となったエラー。|

## <a name="remarks"></a>Remarks

クラス`CInternetException`には、2つのパブリックデータメンバーが含まれています。1つは例外に関連付けられたエラーコードを保持し、もう1つはエラーに関連付けられたインターネットアプリケーションのコンテキスト識別子を保持します。

インターネットアプリケーションのコンテキスト識別子の詳細については、「 [WinInet を使用したインターネットプログラミング](../../mfc/win32-internet-extensions-wininet.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxinet.h

##  <a name="cinternetexception"></a>CInternetException:: CInternetException

このメンバー関数は、 `CInternetException`オブジェクトが作成されるときに呼び出されます。

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>パラメーター

*dwError*<br/>
例外の原因となったエラー。

### <a name="remarks"></a>Remarks

CInternetException をスローするには、MFC グローバル関数[AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)を呼び出します。

##  <a name="m_dwcontext"></a>  CInternetException::m_dwContext

関連するインターネット操作に関連付けられたコンテキスト値。

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Remarks

コンテキスト識別子は、最初は[CInternetSession](../../mfc/reference/cinternetsession-class.md)で指定され、MFC によって[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)クラスと[CInternetFile](../../mfc/reference/cinternetfile-class.md)派生クラスに渡されます。 この既定値を上書きし、任意の*dwContext*パラメーターに任意の値を割り当てることができます。 *dwContext*は、指定されたオブジェクトのすべての操作に関連付けられています。 *dwContext*は、 [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)によって返される操作の状態情報を識別します。

##  <a name="m_dwerror"></a>CInternetException:: m_dwError

例外の原因となったエラー。

```
DWORD m_dwError;
```

### <a name="remarks"></a>Remarks

このエラー値は、WINERROR.H にあるシステムエラーコードの可能性があります。H、または WININET からのエラー値。始め.

Win32 エラーコードの一覧については、「[エラーコード](/windows/win32/Debug/system-error-codes)」を参照してください。 インターネット固有のエラーメッセージの一覧については、「」を参照してください。 両方のトピックは Windows SDK にあります。

## <a name="see-also"></a>関連項目

[CException クラス](../../mfc/reference/cexception-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CException クラス](../../mfc/reference/cexception-class.md)
