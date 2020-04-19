---
title: AFX_EXTENSION_MODULE 構造体
ms.date: 11/04/2016
f1_keywords:
- AFX_EXTENSION_MODULE
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
ms.openlocfilehash: e1bdc9d744424ab0ad59be3bd7b815b5122bcd10
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338637"
---
# <a name="afxextensionmodule-structure"></a>AFX_EXTENSION_MODULE 構造体

`AFX_EXTENSION_MODULE` MFC 拡張 DLL のモジュールの状態を保持する MFC 拡張 Dll の初期化中に使用されます。

## <a name="syntax"></a>構文

```
struct AFX_EXTENSION_MODULE
{
    BOOL bInitialized;
    HMODULE hModule;
    HMODULE hResource;
    CRuntimeClass* pFirstSharedClass;
    COleObjectFactory* pFirstSharedFactory;
};
```

#### <a name="parameters"></a>パラメーター

*bInitialized*<br/>
DLL モジュールがで初期化された場合は TRUE。`AfxInitExtensionModule`します。

*hModule*<br/>
DLL のモジュールのハンドルを指定します。

*hResource*<br/>
DLL のカスタム リソース モジュールのハンドルを指定します。

*pFirstSharedClass*<br/>
情報へのポインター (、`CRuntimeClass`構造) DLL モジュールの最初のランタイム クラスの概要。 ランタイム クラスの一覧の先頭を指定するために使用します。

*pFirstSharedFactory*<br/>
DLL モジュールの最初のオブジェクト ファクトリへのポインター (、`COleObjectFactory`オブジェクト)。 クラス ファクトリの一覧の先頭を指定するために使用します。

## <a name="remarks"></a>Remarks

MFC 拡張 Dll の 2 つの作業を実行しなければ、`DllMain`関数。

- 呼び出す[AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)戻り値を確認します。

- 作成、`CDynLinkLibrary`オブジェクトのかどうか、DLL をエクスポート[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトか、独自のカスタム リソース。

`AFX_EXTENSION_MODULE`構造が MFC 拡張 DLL のモジュールの状態、実行する前に通常の静的オブジェクトの構築の一部としてに MFC 拡張 DLL が初期化されたランタイム クラスのオブジェクトのコピーを含むのコピーを保持するために使用される`DllMain`は入力します。 例えば:

[!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]

格納されているモジュールの情報、`AFX_EXTENSION_MODULE`構造にコピーできる、`CDynLinkLibrary`オブジェクト。 例:

[!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]

## <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

## <a name="see-also"></a>関連項目

[構造体、スタイル、コールバック関数とメッセージ マップ](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)<br/>
[AfxTermExtensionModule](extension-dll-macros.md#afxtermextensionmodule)
