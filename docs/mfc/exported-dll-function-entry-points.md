---
title: DLL のエクスポート関数のエントリ ポイント
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [MFC], functions
- MFC, managing state data
- state management [MFC], exported DLLs
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
ms.openlocfilehash: 129defe39a79fd38211a539a4a85d79d9a3c0998
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405912"
---
# <a name="exported-dll-function-entry-points"></a>DLL のエクスポート関数のエントリ ポイント

DLL のエクスポートされた関数を使用して、 [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) DLL モジュールから呼び出し元アプリケーションの DLL に切り替える場合は、適切なグローバル状態を維持するためにマクロ。

呼び出されると、このマクロは、設定`pModuleState`へのポインター、`AFX_MODULE_STATE`関数のコンテナーのスコープの残りの部分の有効なモジュールの状態と、モジュールのグローバル データを含む構造体。 マクロを含むスコープから離れると、前のモジュールの状態は自動的に復元します。

インスタンスを構築することによってこの切り替えを行う、`AFX_MODULE_STATE`スタック上のクラス。 コンス トラクターにこのクラスは現在のモジュール状態へのポインターを取得しますと、メンバー変数に格納し、設定`pModuleState`として新しいモジュールの状態。 デストラクターでは、このクラスは、有効なモジュールの状態とそのメンバー変数に格納されているポインターを復元します。

DLL のダイアログ ボックスを起動するなど、エクスポートされた関数がある場合は、関数の先頭に次のコードを追加する必要があります。

[!code-cpp[NVC_MFCConnectionPoints#6](../mfc/codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]

モジュールの現在の状態から返された状態と交換この[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)現在のスコープが終わるまでです。

Dll 内のリソースの問題が発生する場合、`AFX_MANAGE_STATE`マクロは使用されません。 既定では、MFC では、メイン アプリケーションのリソース ハンドルを使用して、リソースのテンプレートを読み込みます。 このテンプレートは、DLL に実際に格納されます。 根本原因は、MFC のモジュールの状態情報がによって切り替えられたいないこと、`AFX_MANAGE_STATE`マクロ。 リソース ハンドルが MFC のモジュール状態から復旧します。 モジュールの状態が切り替えられていないすると、間違ったリソース ハンドルが使用されます。

`AFX_MANAGE_STATE` DLL 内の各関数に入力する必要はありません。 たとえば、`InitInstance`ことがなくアプリケーションの MFC コードから呼び出すことが`AFX_MANAGE_STATE`MFC モジュールの直前の状態を自動的に移動するため、`InitInstance`とスイッチの後のバックアップを作成し`InitInstance`を返します。 すべてのメッセージ マップ ハンドラーも同様です。 レギュラー MFC Dll があるすべてのメッセージをルーティングする前に、モジュールの状態を自動的に切り替わる特殊なマスター ウィンドウ プロシージャ。

## <a name="see-also"></a>関連項目

[MFC モジュールの状態データの管理](../mfc/managing-the-state-data-of-mfc-modules.md)
