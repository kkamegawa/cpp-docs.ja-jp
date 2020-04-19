---
title: 'CAtlServiceModuleT:: ServiceMain 関数'
ms.date: 11/04/2016
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: b79767d4c1696174f90a325ea152ccc7939ed9fe
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491722"
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT:: ServiceMain 関数

サービスコントロールマネージャー (SCM) は、 `ServiceMain`コントロールパネルの サービス アプリケーションを開いてサービスを選択し、**開始** をクリックしたときにを呼び出します。

Scm がを呼び出し`ServiceMain`た後、サービスは scm にハンドラー関数を与える必要があります。 この関数を使用すると、SCM はサービスの状態を取得し、特定の命令 (一時停止や停止など) を渡すことができます。 SCM は、サービスが Win32 API 関数[RegisterServiceCtrlHandler](/windows/win32/api/winsvc/nf-winsvc-registerservicectrlhandlerw)に`_Handler`渡すときに、この関数を取得します。 (`_Handler`は静的でないメンバー関数[ハンドラー](../atl/reference/catlservicemodulet-class.md#handler)を呼び出す静的メンバー関数です)。

サービスは起動時に、現在の状態を SCM に通知する必要があります。 これを行うには、SERVICE_START_PENDING 関数 Win32 API の[SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus)にを渡します。

`ServiceMain`次に`CAtlExeModuleT::InitializeCom`、Win32 API 関数[CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex)を呼び出すを呼び出します。 既定では`InitializeCom` 、は COINIT_MULTITHREADED フラグを関数に渡します。 このフラグは、プログラムがフリースレッドサーバーであることを示します。

ここで`CAtlServiceModuleT::Run` 、は、サービスの主要な作業を実行するために呼び出されます。 `Run`は、サービスが停止するまで実行を続けます。

## <a name="see-also"></a>関連項目

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT:: ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)
