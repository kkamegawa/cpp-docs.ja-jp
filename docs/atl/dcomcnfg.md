---
title: DCOMCNFG
ms.date: 11/04/2016
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
ms.openlocfilehash: a389a46cd02b40cef46d687743fd3416cc4f3154
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250785"
---
# <a name="dcomcnfg"></a>DCOMCNFG

Dcomcnfg」とは、レジストリでさまざまな DCOM に固有の設定を構成することを許可する Windows NT 4.0 ユーティリティです。 DCOMCNFG ウィンドウには、3 つのページがあります。既定のセキュリティ、既定のプロパティ、およびアプリケーション。 Windows 2000 では、4 番目のページであり、既定のプロトコル は存在します。

## <a name="default-security-page"></a>既定のセキュリティ ページ

既定のセキュリティ ページを使用すると、システムのオブジェクトの既定のアクセス許可を指定します。 既定のセキュリティ ページには、3 つのセクションがあります。アクセス、起動、および構成します。 セクションの既定値を変更するには、対応するをクリックします。**既定値の編集**ボタンをクリックします。 これらの既定のセキュリティ設定が下のレジストリに格納されている`HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`します。

## <a name="default-protocols-page"></a>既定のプロトコル ページ

このページには、このコンピューターで DCOM を使用可能なネットワーク プロトコルのセットが一覧表示されます。 順序で使用されます。 優先順位が反映されます。一覧の最初では、最高の優先順位を持ちます。 プロトコルを追加またはこのページから削除できます。

## <a name="default-properties-page"></a>既定のプロパティ ページ

既定のプロパティ ページで、選択する必要があります、**このコンピューター上で分散 COM を有効にする**チェック ボックスをこのマシンで実行されているオブジェクトを COM へのアクセスを他のマシン上のクライアントの場合。 このオプションの設定を選択すると、`HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM`値を`Y`します。

## <a name="applications-page"></a>[アプリケーション] ページ

アプリケーションのページで、特定のオブジェクトの設定を変更します。 単に一覧からアプリケーションを選択し、クリックして、**プロパティ**ボタンをクリックします。 [プロパティ] ウィンドウには、5 つのページがあります。

- [全般] ページでは、使用しているアプリケーションを確認します。

- 場所 ページでは、アプリケーションがクライアントを呼び出すときに実行する必要がありますを指定できます。`CoCreateInstance`に関連する CLSID。 選択した場合、**次のコンピューターでアプリケーションを実行**チェック ボックスをオンし、コンピューター名を入力し、`RemoteServerName`値がそのアプリケーションの AppID の下に追加されます。 オフにすると、**このコンピューターでアプリケーションを実行** チェック ボックスの名前変更、`LocalService`値を`_LocalService`と、これによって、無効にします。

- セキュリティ ページは、DCOMCNFG ウィンドウにある既定のセキュリティ ページに似ていますが、これらの設定は、現在のアプリケーションにのみ適用されます。 ここでも、そのオブジェクトの AppID の下の設定が格納されます。

- ユーザーがアプリケーションの実行に使用される特定のページを識別します。

- [エンドポイント] ページには、プロトコルと選択した DCOM サーバーのクライアントで使用するために使用可能なエンドポイントのセットが一覧表示します。

## <a name="see-also"></a>関連項目

[Services](../atl/atl-services.md)
