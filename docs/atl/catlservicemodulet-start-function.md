---
title: 'CAtlServiceModuleT:: Start 関数'
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: e6de15f40e89bfffba504db04ee7a16b2a68cac9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491666"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT:: Start 関数

サービスが実行されると`_tWinMain` 、 `CAtlServiceModuleT::WinMain`はを呼び出し、は`CAtlServiceModuleT::Start`を呼び出します。

`CAtlServiceModuleT::Start`各サービスをスタートアップ関数`SERVICE_TABLE_ENTRY`にマップする構造体の配列を設定します。 この配列は、Win32 API 関数[startservicectrldispatcher に](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw)に渡されます。 理論的には、1つの EXE が複数のサービスを処理でき`SERVICE_TABLE_ENTRY` 、配列に複数の構造体が含まれる可能性があります。 ただし、ATL によって生成されるサービスでは、実行可能ファイルごとに1つのサービスのみがサポートされます。 したがって、配列には、サービス名と`_ServiceMain`スタートアップ関数の1つのエントリがあります。 `_ServiceMain`は、静的でないメンバー `CAtlServiceModuleT`関数を`ServiceMain`呼び出すの静的メンバー関数です。

> [!NOTE]
>  `StartServiceCtrlDispatcher`サービスコントロールマネージャー (SCM) に接続できなかった場合は、プログラムがサービスとして実行されていないことを意味します。 この場合、プログラムは直接を`CAtlServiceModuleT::Run`呼び出して、プログラムをローカルサーバーとして実行できるようにします。 ローカルサーバーとしてプログラムを実行する方法の詳細については、「[デバッグのヒント](../atl/debugging-tips.md)」を参照してください。

## <a name="see-also"></a>関連項目

[Services](../atl/atl-services.md)<br/>
[CAtlServiceModuleT:: Start](../atl/reference/catlservicemodulet-class.md#start)
