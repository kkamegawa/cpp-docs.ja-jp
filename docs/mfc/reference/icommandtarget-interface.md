---
title: ICommandTarget インターフェイス
ms.date: 11/04/2016
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
ms.openlocfilehash: a224b868ea1923bb4f84b0d682c71fadb63da572
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322070"
---
# <a name="icommandtarget-interface"></a>ICommandTarget インターフェイス

コマンド ソース オブジェクトからのコマンドを受信するインターフェイスを使用するユーザー コントロールを提供します。

## <a name="syntax"></a>構文

```
interface class ICommandTarget
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[ICommandTarget::Initialize](#initialize)|コマンド ターゲット オブジェクトを初期化します。|

## <a name="remarks"></a>Remarks

MFC ビューでユーザー コントロールをホストするときに[CWinFormsView](../../mfc/reference/cwinformsview-class.md)ルート コマンドおよび更新コマンド UI メッセージをユーザー コントロールを MFC のコマンド (たとえば、フレームのメニュー項目やツールバーのボタン) を処理できるようにします。 実装することによって`ICommandTarget`、ユーザー コントロールへの参照を提供する、 [ICommandSource](../../mfc/reference/icommandsource-interface.md)オブジェクト。

「[方法:Windows フォーム コントロールにコマンド ルーティングを追加](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)を使用する方法の例については`ICommandTarget`します。

Windows フォームの使用に関する詳細については、次を参照してください。 [MFC における Windows フォーム ユーザー コントロールを使用して](../../dotnet/using-a-windows-form-user-control-in-mfc.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwinforms.h (アセンブリ atlmfc\lib\mfcmifc80.dll で定義)

##  <a name="initialize"></a> ICommandTarget::Initialize

コマンド ターゲット オブジェクトを初期化します。

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>パラメーター

*cmdSource*<br/>
コマンド ソース オブジェクトへのハンドル。

### <a name="remarks"></a>Remarks

MFC ビューでユーザー コントロールをホストする場合、CWinFormsView は MFC のコマンドを処理することを許可するユーザー コントロールにコマンドおよび更新コマンド UI メッセージをルーティングします。

このメソッドは、コマンド ターゲット オブジェクトを初期化し、指定したコマンドのソース オブジェクト cmdSource に関連付けます。 ユーザー コントロール クラスの実装で呼び出す必要があります。 初期化時に、呼び出し元の ICommandSource::AddCommandHandler Initialize 実装では、コマンド ソース オブジェクトとコマンド ハンドラーを登録してください。 表示する方法。これを実行する初期化を使用する方法の例については、Windows フォーム コントロールにコマンド ルーティングを追加します。

## <a name="see-also"></a>関連項目

[方法: Windows フォーム コントロールにコマンド ルーティングを追加する](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandSource インターフェイス](../../mfc/reference/icommandsource-interface.md)
