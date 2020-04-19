---
title: プロバイダーのサービスの有効化と無効化
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: d91f08accf1a8be69f63d6bbcaa4c620d68c1077
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175451"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>プロバイダーのサービスの有効化と無効化

各 OLE DB サービスを有効になっているまたは 1 つのプロバイダーにアクセスするすべてのアプリケーションに対して既定で無効になっていることができます。 これは、次の表に示すように、有効または無効にすると、サービスを指定する DWORD 値プロバイダーの CLSID、下の OLEDB_SERVICES レジストリ エントリを追加することで行います。

|既定のサービスを有効になっています。|キーワードの値|
|------------------------------|-------------------|
|すべてのサービス (既定値)|0 xffffffff|
|プールを除くすべてと自動確保|0xfffffffe|
|クライアント カーソルを除くすべて|0xfffffffb|
|プールで自動確保、およびクライアント カーソルを除くすべて|0xfffffff0|
|サービスはありません。|0x00000000|
|集計、すべてのサービス使用不可|\<見つからないキー >|

## <a name="see-also"></a>関連項目

[OLE DB サービスの有効化と無効化](../../data/oledb/enabling-and-disabling-ole-db-services.md)