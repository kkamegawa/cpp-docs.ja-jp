---
title: レジストリ エントリ (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
ms.openlocfilehash: 7a89bc5d510d493f557b7ea74b8eabe5dfd87ac1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196756"
---
# <a name="registry-entries"></a>レジストリ エントリ

DCOM には、アプリケーション Id (Appid)、レジストリで一元的な場所に 1 つまたは複数の DCOM オブジェクトの構成オプションをグループ化の概念が導入されました。 AppID を指定するには、という名前の下にあるオブジェクトの CLSID 値 AppID の値を示します。

既定では、ATL によって生成されたサービスは、GUID としての AppID の CLSID を使用します。  `HKEY_CLASSES_ROOT\AppID`DCOM に固有のエントリを指定することができます。 最初に、2 つのエントリが存在します。

- `LocalService`、、サービスの名前と同じ値です。 この値が存在する場合は、代わりに使用、 `LocalServer32` CLSID 下キー。

- `ServiceParameters`を値と等しい`-Service`します。 この値は、実行しているサービスに渡されるパラメーターを指定します。 これらのパラメーターは、サービスに渡される注`ServiceMain`機能しない`WinMain`します。

DCOM サービスも下のもう 1 つのキーを作成する必要がある`HKEY_CLASSES_ROOT\AppID`します。 このキーであり、exe ファイルの名前に等しい AppID エントリを指す、AppID 値が含まれているため、相互参照として機能します。

## <a name="see-also"></a>関連項目

[Services](../atl/atl-services.md)
