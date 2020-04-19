---
title: ATL プロジェクトで MFC サポート
ms.date: 11/04/2016
f1_keywords:
- vc.atl.addmfc
helpviewer_keywords:
- ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
ms.openlocfilehash: 0aece6805f1de987b0164f405e50b99fd706fef4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275426"
---
# <a name="mfc-support-in-atl-projects"></a>ATL プロジェクトで MFC サポート

選択した場合**サポート MFC** ATL プロジェクト ウィザードで、プロジェクトは、MFC アプリケーション オブジェクト (クラス) としてアプリケーションを宣言します。 プロジェクトが MFC ライブラリを初期化し、クラスをインスタンス化します (クラス*ProjName*) から派生する[CWinApp](../../mfc/reference/cwinapp-class.md)します。

このオプションは、属性なし ATL DLL プロジェクトにのみ使用できます。

```
class CProjNameApp : public CWinApp
{
public:

// Overrides
    virtual BOOL InitInstance();
virtual int ExitInstance();
DECLARE_MESSAGE_MAP()
};

BEGIN_MESSAGE_MAP(CProjNameApp, CWinApp)
END_MESSAGE_MAP()

CProjNameApp theApp;

BOOL CProjNameApp::InitInstance()
{
    return CWinApp::InitInstance();

}

int CProjNameApp::ExitInstance()
{
    return CWinApp::ExitInstance();

}
```

アプリケーションのオブジェクト クラスを表示することができ、その`InitInstance`と`ExitInstance`クラス ビュー内の関数。

## <a name="see-also"></a>関連項目

[クラスの追加](../../ide/adding-a-class-visual-cpp.md)<br/>
[ATL プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)<br/>
[ATL プロジェクトの既定の構成](../../atl/reference/default-atl-project-configurations.md)
