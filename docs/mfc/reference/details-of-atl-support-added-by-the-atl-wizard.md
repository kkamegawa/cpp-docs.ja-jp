---
title: ATL ウィザードで追加した ATL サポートの詳細
ms.date: 08/20/2019
f1_keywords:
- vc.codewiz.atl.support
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
ms.openlocfilehash: 10bafc9bd06ee94398f91d5af478a6e1cd7ca617
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108454"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>ATL ウィザードで追加した ATL サポートの詳細

::: moniker range=">=vs-2019"

既存の[MFC 実行可能ファイルまたは DLL に atl サポートを追加](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)すると、Visual Studio によって既定では、*フレームワーク*と`#include` `#define`いう名前のヘッダーファイルが追加されます。このヘッダーファイルには、プロジェクトで atl を使用できるようにするプリプロセッサディレクティブが含まれています。 以前のバージョンの Visual Studio で行ったように、追加のファイルやクラスは追加されません。

::: moniker-end

::: moniker range="<=vs-2017"

既存の[mfc 実行可能ファイルまたは DLL に ATL サポートを追加](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)すると、Visual Studio によって既存の mfc プロジェクトが次のように変更さ`MFCEXE`れます (この例では、プロジェクトが呼び出されます)。

- 2つの新しいファイル (サーバーの登録に使用される .idl ファイルと .rgs ファイル) が追加されます。

- メインアプリケーションのヘッダーおよび実装ファイル (mfcexe .h と mfcexe .cpp) では、(から`CAtlMFCModule`派生した) 新しいクラスが追加されます。 新しいクラスに加えて、コードは登録のため`InitInstance`にに追加されています。 また、クラスオブジェクトを取り消す`ExitInstance`ために、関数にコードが追加されます。 最後に、ヘッダーファイルに2つの新しいヘッダーファイル (initguid と Mfcexe_i) が実装ファイルに含まれており、派生クラスの`CAtlMFCModule`新しい guid を宣言して初期化しています。

- サーバーを適切に登録するために、新しい .rgs ファイルのエントリがプロジェクトのリソースファイルに追加されます。

::: moniker-end

## <a name="notes-for-dll-projects"></a>DLL プロジェクトのメモ

MFC DLL プロジェクトに ATL サポートを追加すると、いくつかの相違点が表示されます。 DLL を登録および登録`DLLRegisterServer`解除`DLLUnregisterServer`するためのおよび関数にコードが追加されました。 コードは[DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow)と[DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject)にも追加されます。

## <a name="see-also"></a>関連項目

[MFC プロジェクトでの ATL のサポート](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[コード ウィザードを使用した機能の追加](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[クラスの追加](../../ide/adding-a-class-visual-cpp.md)<br/>
[メンバー関数の追加](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[メンバー変数の追加](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[仮想関数のオーバーライド](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC メッセージ ハンドラー](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[クラス各部へのジャンプ](../../ide/navigate-code-cpp.md)
