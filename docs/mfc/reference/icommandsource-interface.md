---
title: ICommandSource インターフェイス
ms.date: 03/27/2019
f1_keywords:
- ICommandSource
- AFXWINFORMS/ICommandSource
- AFXWINFORMS/ICommandSource::AddCommandHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::AddCommandUIHandler
- AFXWINFORMS/ICommandSource::PostCommand
- AFXWINFORMS/ICommandSource::RemoveCommandHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::RemoveCommandUIHandler
- AFXWINFORMS/ICommandSource::SendCommand
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
ms.openlocfilehash: eed7abbbb40c532ad596f683b6ed2c98a0cadf9b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322083"
---
# <a name="icommandsource-interface"></a>ICommandSource インターフェイス

ユーザー コントロールにコマンドのソース オブジェクトから送信されたコマンドを管理します。

## <a name="syntax"></a>構文

```
interface class ICommandSource
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[ICommandSource::AddCommandHandler](#addcommandhandler)|コマンド ソース オブジェクトには、コマンド ハンドラーを追加します。|
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|コマンド ソース オブジェクトには、一連のコマンド ハンドラーを追加します。|
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|コマンド ソース オブジェクトには、一連のユーザー インターフェイス コマンド メッセージ ハンドラーを追加します。|
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|コマンド ソース オブジェクトには、ユーザー インターフェイス コマンド メッセージのハンドラーを追加します。|
|[ICommandSource::PostCommand](#postcommand)|処理するを待つことがなく、メッセージを送信します。|
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|コマンド ソース オブジェクトから、コマンド ハンドラーを削除します。|
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|コマンド ソース オブジェクトから、コマンド ハンドラーのグループを削除します。|
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|コマンド ソース オブジェクトからのユーザー インターフェイス コマンド メッセージ ハンドラーのグループを削除します。|
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|コマンド ソース オブジェクトからのユーザー インターフェイス コマンド メッセージのハンドラーを削除します。|
|[ICommandSource::SendCommand](#sendcommand)|メッセージを送信し、返す前に処理されるまで待機します。|

### <a name="remarks"></a>Remarks

MFC ビューでユーザー コントロールをホストするときに[CWinFormsView クラス](../../mfc/reference/cwinformsview-class.md)ルート コマンドおよび更新コマンド UI メッセージをユーザー コントロールを MFC のコマンド (たとえば、フレームのメニュー項目やツールバーのボタン) を処理できるようにします。 実装することによって[ICommandTarget インターフェイス](../../mfc/reference/icommandtarget-interface.md)、ユーザー コントロールへの参照を提供する、`ICommandSource`オブジェクト。

「[方法:Windows フォーム コントロールにコマンド ルーティングを追加](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)を使用する方法の例については`ICommandTarget`します。

Windows フォームの使用に関する詳細については、次を参照してください。 [MFC における Windows フォーム ユーザー コントロールを使用して](../../dotnet/using-a-windows-form-user-control-in-mfc.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwinforms.h (アセンブリ atlmfc\lib\mfcmifc80.dll で定義)

## <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler

コマンド ソース オブジェクトには、コマンド ハンドラーを追加します。
```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>パラメーター

*cmdID*<br/>
コマンド ID。
*cmdHandler*<br/>
コマンド ハンドラー メソッドへのハンドル。

### <a name="remarks"></a>Remarks

このメソッドは、コマンド ソース オブジェクトにコマンド ハンドラーの cmdHandler を追加し、cmdID ハンドラーにマップします。
「[方法:Windows フォーム コントロールにコマンド ルーティングを追加](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)AddCommandHandler を使用する方法の例についてはします。

## <a name="addcommandrangehandler"></a> ICommandSource::AddCommandRangeHandler

コマンド ソース オブジェクトには、一連のコマンド ハンドラーを追加します。
```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>パラメーター

*cmdIDMin*<br/>
コマンドの ID 範囲の開始インデックス。
*cmdIDMax*<br/>
コマンドの ID 範囲の終了インデックス。
*cmdHandler*<br/>
コマンドがマップされているメッセージのハンドラー メソッドへのハンドル。
### <a name="remarks"></a>Remarks

このメソッドは、コマンド Id の連続する範囲を 1 つのメッセージ ハンドラーにマップし、コマンド ソース オブジェクトに追加します。 これは、1 つのメソッドを使用して関連するボタンのグループを処理するために使用されます。

## <a name="addcommandrangeuihandler"></a> ICommandSource::AddCommandRangeUIHandler

コマンド ソース オブジェクトには、一連のユーザー インターフェイス コマンド メッセージ ハンドラーを追加します。
```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>パラメーター

*cmdIDMin*<br/>
コマンドの ID 範囲の開始インデックス。
*cmdIDMax*<br/>
コマンドの ID 範囲の終了インデックス。
*cmdHandler*<br/>
コマンドがマップされているメッセージのハンドラー メソッドへのハンドル。

### <a name="remarks"></a>Remarks

このメソッドは、コマンド Id の連続する範囲を 1 人のユーザー インターフェイス コマンド メッセージのハンドラーにマップし、コマンド ソース オブジェクトに追加します。 これは、1 つのメソッドを使用して関連するボタンのグループを処理するために使用されます。

## <a name="addcommanduihandler"></a> ICommandSource::AddCommandUIHandler

コマンド ソース オブジェクトには、ユーザー インターフェイス コマンド メッセージのハンドラーを追加します。
```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>パラメーター

*cmdID*<br/>
コマンド ID。
*cmdUIHandler*<br/>
ユーザー インターフェイス コマンド メッセージのハンドラー メソッドへのハンドル。

### <a name="remarks"></a>Remarks

このメソッドは、コマンド ソース オブジェクトにユーザー インターフェイス コマンド メッセージ ハンドラー cmdHandler を追加し、cmdID ハンドラーにマップします。

## <a name="postcommand"></a> ICommandSource::PostCommand

処理するを待つことがなく、メッセージを送信します。
```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>パラメーター

*command*<br/>
投稿するメッセージのコマンド ID。
### <a name="remarks"></a>Remarks

このメソッドは、コマンドで指定した ID にマップされているメッセージを非同期的にポストします。 ウィンドウのメッセージ キューにメッセージを配置する CWnd::PostMessage を呼び出し、対応するウィンドウ メッセージを処理するを待たずに戻ります。

## <a name="removecommandhandler"></a> ICommandSource::RemoveCommandHandler

コマンド ソース オブジェクトから、コマンド ハンドラーを削除します。
```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>パラメーター

*cmdID*<br/>
コマンド ID。
### <a name="remarks"></a>Remarks

このメソッドは、コマンド ソース オブジェクトから cmdID に割り当てられたコマンド ハンドラーを削除します。

## <a name="removecommandrangehandler"></a> ICommandSource::RemoveCommandRangeHandler

コマンド ソース オブジェクトから、コマンド ハンドラーのグループを削除します。
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>パラメーター

*cmdIDMin*<br/>
コマンドの ID 範囲の開始インデックス。
*cmdIDMax*<br/>
コマンドの ID 範囲の終了インデックス。
### <a name="remarks"></a>Remarks

このメソッドは、メッセージ ハンドラーを cmdIDMin およびコマンド ソース オブジェクトからの cmdIDMax で指定したコマンド Id にマップのグループを削除します。

## <a name="removecommandrangeuihandler"></a> ICommandSource::RemoveCommandRangeUIHandler

コマンド ソース オブジェクトからのユーザー インターフェイス コマンド メッセージ ハンドラーのグループを削除します。
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>パラメーター

*cmdIDMin*<br/>
コマンドの ID 範囲の開始インデックス。
*cmdIDMax*<br/>
コマンドの ID 範囲の終了インデックス。
### <a name="remarks"></a>Remarks

このメソッドは、cmdIDMin およびコマンド ソース オブジェクトからの cmdIDMax で指定したコマンド Id にマップされている、ユーザー インターフェイス コマンド メッセージ ハンドラーのグループを削除します。

## <a name="removecommanduihandler"></a> ICommandSource::RemoveCommandUIHandler

コマンド ソース オブジェクトからのユーザー インターフェイス コマンド メッセージのハンドラーを削除します。
```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>パラメーター

*cmdID*<br/>
コマンド ID。
### <a name="remarks"></a>Remarks

このメソッドは、コマンド ソース オブジェクトから cmdID に割り当てられたユーザー インターフェイス コマンドのメッセージ ハンドラーを削除します。

## <a name="sendcommand"></a> ICommandSource::SendCommand

メッセージを送信し、返す前に処理されるまで待機します。
```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>パラメーター

*command*<br/>
送信されるメッセージのコマンド ID。
### <a name="remarks"></a>Remarks

このメソッドは、コマンドで指定した ID にマップされているメッセージを同期的に送信します。 そのウィンドウ プロシージャが返す前にメッセージを処理するまで待機し、ウィンドウのメッセージ キューにメッセージを配置する CWnd::SendMessage の呼び出し。
## <a name="see-also"></a>関連項目

[方法: Windows フォーム コントロールにコマンド ルーティングを追加する](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[ICommandTarget インターフェイス](../../mfc/reference/icommandtarget-interface.md)
