---
title: OLE の初期化
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 6860697dd3adbe26197dd9075e84f402029e00a5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502022"
---
# <a name="ole-initialization"></a>OLE の初期化

アプリケーションで OLE system サービスを使用するには、OLE システム Dll を初期化し、Dll が正しいバージョンであることを確認する必要があります。 関数`AfxOleInit`は、OLE システム dll を初期化します。

### <a name="ole-initialization"></a>OLE の初期化

|||
|-|-|
|[AfxOleInit](#afxoleinit)|OLE ライブラリを初期化します。|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|OLE コントロールのコンテインメントのサポートを有効`InitInstance`にするには、アプリケーションオブジェクトの関数でこの関数を呼び出します。|

## <a name="afxenablecontrolcontainer"></a>AfxEnableControlContainer

OLE コントロールのコンテインメントのサポートを有効`InitInstance`にするには、アプリケーションオブジェクトの関数でこの関数を呼び出します。

### <a name="syntax"></a>構文

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Remarks

OLE コントロール (現在は ActiveX コントロールと呼ばれます) の詳細については、「 [Activex コントロールのトピック](../mfc-activex-controls.md)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

##  <a name="afxoleinit"></a>AfxOleInit

アプリケーションの OLE サポートを初期化します。

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>戻り値

成功した場合は 0 以外の値です。初期化に失敗した場合は 0 です。失敗の原因は多くの場合、正しくないバージョンの OLE システム DLL がインストールされていることです。

### <a name="remarks"></a>Remarks

MFC アプリケーションに対する OLE サポートを初期化するには、この関数を呼び出します。 この関数を呼び出すと、次のアクションが発生します。

- 呼び出し元のアプリケーションの現在のアパートメントで COM ライブラリを初期化します。 詳細については、「 [Oleinitialize](/windows/win32/api/ole2/nf-ole2-oleinitialize)」を参照してください。

- [の imessagefilter.prefiltermessage](/windows/win32/api/objidl/nn-objidl-imessagefilter)インターフェイスを実装して、メッセージフィルターオブジェクトを作成します。 このメッセージフィルターには、 [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)の呼び出しを使用してアクセスできます。

> [!NOTE]
>  **AfxOleInit**が MFC DLL から呼び出された場合、呼び出しは失敗します。 この関数は DLL から呼び出された場合、呼び出し元アプリケーションによって OLE システムが既に初期化されていることを想定するため、失敗が生じます。

> [!NOTE]
>  MFC アプリケーションは、シングルスレッド アパートメント (STA) として初期化する必要があります。 `InitInstance`オーバーライドで[CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex)を呼び出した場合は、COINIT_APARTMENTTHREADED (COINIT_MULTITHREADED ではなく) を指定します。

### <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
