---
title: ATL の概要
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM objects, creating in ATL
- ATL
ms.assetid: 77f565e8-c4ec-4a80-af4b-7278fcfe5c98
ms.openlocfilehash: 5eba816bc87eeebea2c41489a5d15c48645739e8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492109"
---
# <a name="introduction-to-atl"></a>ATL の概要

ATL は、小規模で高速のコンポーネントオブジェクトモデル ( C++ COM) オブジェクトを簡単に作成できるテンプレートベースのクラスのセット Active Template Library です。 これには、 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)、 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)、 [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)、および`IDispatch`の2つのインターフェイスのストック実装、標準の com 列挙子インターフェイス、接続ポイント、ティアオフなど、主要な com 機能が特別にサポートされています。インターフェイスおよび ActiveX コントロール。

ATL コードを使用すると、シングルスレッドオブジェクト、アパートメントモデルオブジェクト、フリースレッドモデルオブジェクト、またはフリースレッドオブジェクトとアパートメントモデルオブジェクトの両方を作成できます。

このセクションでは、次のトピックについて説明します。

- [テンプレートライブラリ](../atl/using-a-template-library.md)と標準ライブラリの違いについて説明します。

- [ATL でできることとできない](../atl/scope-of-atl.md)こと。

- [ATL と MFC の選択に関する推奨事項](../atl/recommendations-for-choosing-between-atl-and-mfc.md)。

## <a name="see-also"></a>関連項目

[COM と ATL の概要](../atl/introduction-to-com-and-atl.md)
