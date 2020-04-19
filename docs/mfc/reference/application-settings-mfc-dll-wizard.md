---
title: '[アプリケーションの設定] (MFC DLL ウィザード)'
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.dll.appset
helpviewer_keywords:
- MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
ms.openlocfilehash: f021f2023af839413306c1e3d56dc741749cf216
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152047"
---
# <a name="application-settings-mfc-dll-wizard"></a>[アプリケーションの設定] (MFC DLL ウィザード)

MFC DLL ウィザードのこのページを使用すると、設計し、新しい MFC DLL プロジェクトに基本的な機能を追加します。

## <a name="dll-type"></a>[DLL の種類]

作成する DLL の種類を選択します。

- **使用して、レギュラー MFC DLL が MFC DLL を共有**

   MFC ライブラリが共有 DLL としてプログラムをリンクするには、このオプションを選択します。 このオプションを使用して、DLL と呼び出し元のアプリケーション間での MFC オブジェクトを共有できません。 プログラムでは、実行時に、MFC ライブラリへの呼び出しが。 このオプションは、MFC ライブラリを使用する複数の実行ファイルで構成される場合に、プログラムのディスクとメモリの量を削減します。 Win32、MFC の両方のプログラムは、DLL で関数を呼び出すことができます。 この種類のプロジェクトで MFC DLL を再配布する必要があります。

- **MFC でのレギュラー MFC DLL が静的にリンク**

   MFC ライブラリをビルド時にプログラムを静的にリンクするには、このオプションを選択します。 Win32、MFC の両方のプログラムは、DLL で関数を呼び出すことができます。 このオプションでは、プログラムのサイズが増えますが、中に、この種類のプロジェクトで MFC DLL を再配布する必要はありません。 DLL と、呼び出し元アプリケーションの MFC オブジェクトを共有することはできません。

- **MFC 拡張 DLL**

   場合は、プログラム実行時に、MFC ライブラリへの呼び出しを使用して、DLL と呼び出し元のアプリケーション間での MFC オブジェクトを共有する場合は、このオプションを選択します。 このオプションは、MFC ライブラリを使用する複数の実行可能ファイルで構成される場合に、プログラムのディスクとメモリの量を削減します。 MFC プログラムだけでは、DLL で関数を呼び出すことができます。 この種類のプロジェクトで MFC DLL を再配布する必要があります。

## <a name="additional-features"></a>その他の機能

MFC DLL は、オートメーションをサポートするかどうか、および Windows sockets をサポートするかどうかを選択します。

- **オートメーション**

   選択**Automation**別のプログラムで実装されているオブジェクトを操作するプログラム。 選択**Automation**も、プログラムを他のオートメーション クライアントに公開します。 参照してください[Automation](../../mfc/automation.md)詳細についてはします。

- **Windows ソケット**

   プログラムが Windows sockets をサポートしていることを指定するには、このオプションを選択します。 Windows ソケットを使用すると、TCP/IP ネットワーク経由で通信するプログラムを作成できます。

   サポートが作成されるときに、Windows で、MFC DLL のソケット[:initinstance](../../mfc/reference/cwinapp-class.md#initinstance)のソケットの初期化をサポートし、MFC ヘッダー ファイル StdAfx.h AfxSock.h が含まれています。

## <a name="see-also"></a>関連項目

[MFC DLL ウィザード](../../mfc/reference/mfc-dll-wizard.md)<br/>
[MFC DLL プロジェクトの作成](../../mfc/reference/creating-an-mfc-dll-project.md)
