---
title: MFC モジュール状態でのアクティベーション コンテキストのサポート
ms.date: 11/04/2016
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
ms.openlocfilehash: 296df3d2ecec74c5c9a7deef1617298d40243724
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511435"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>MFC モジュール状態でのアクティベーション コンテキストのサポート

MFC では、ユーザーモジュールによって提供されるマニフェストリソースを使用してアクティベーションコンテキストを作成します。 アクティベーションコンテキストの作成方法の詳細については、次のトピックを参照してください。

- [アクティベーションコンテキスト](/windows/win32/SbsCs/activation-contexts)

- [アプリケーションマニフェスト](/windows/win32/SbsCs/application-manifests)

- [アセンブリマニフェスト](/windows/win32/SbsCs/assembly-manifests)

## <a name="remarks"></a>Remarks

これらの Windows SDK のトピックを読むときは、mfc が Windows SDK Activation context API を使用しない点を除いて、MFC アクティベーションコンテキストメカニズムが Windows SDK アクティベーションコンテキストに似ていることに注意してください。

アクティベーションコンテキストは、次の方法で MFC アプリケーション、ユーザー Dll、および MFC 拡張 Dll で動作します。

- MFC アプリケーションは、マニフェストリソースに対してリソース ID 1 を使用します。 この場合、MFC は独自のアクティベーションコンテキストを作成しませんが、既定のアプリケーションコンテキストを使用します。

- MFC ユーザー Dll は、マニフェストリソースに対してリソース ID 2 を使用します。 ここでは、MFC はユーザー DLL ごとにアクティベーションコンテキストを作成するため、異なるユーザー Dll で同じライブラリの異なるバージョンを使用できます (たとえば、コモンコントロールライブラリ)。

- MFC 拡張 Dll は、ホストしているアプリケーションまたはユーザー Dll を使用してアクティベーションコンテキストを確立します。

アクティベーションコンテキストの状態は、「[アクティベーションコンテキスト API の使用](/windows/win32/SbsCs/using-the-activation-context-api)」で説明されているプロセスを使用して変更できますが、MFC アクティベーションコンテキスト機構を使用すると、DLL ベースのプラグインアーキテクチャを簡単に開発できない場合 (または外部プラグインの呼び出しの前後にアクティブ化の状態を手動で切り替えることはできません)。

アクティベーションコンテキストは、 [AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)で作成されます。 `AFX_MODULE_STATE`デストラクターでは破棄されます。 アクティベーションコンテキストハンドルは、 `AFX_MODULE_STATE`に保持されます。 (`AFX_MODULE_STATE`は[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)に記述されています)。

[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)マクロはアクティブ化コンテキストをアクティブ化し、非アクティブ化します。 `AFX_MANAGE_STATE`を使用すると、mfc Dll に加えて、静的な MFC ライブラリに対して、ユーザー DLL によって選択された適切なアクティベーションコンテキストで MFC コードを実行できるようになります。

## <a name="see-also"></a>関連項目

[アクティベーションコンテキスト](/windows/win32/SbsCs/activation-contexts)<br/>
[アプリケーションマニフェスト](/windows/win32/SbsCs/application-manifests)<br/>
[アセンブリマニフェスト](/windows/win32/SbsCs/assembly-manifests)<br/>
[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)<br/>
[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)<br/>
[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)
