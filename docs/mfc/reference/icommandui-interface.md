---
title: ICommandUI インターフェイス
ms.date: 09/07/2019
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
ms.openlocfilehash: a7bb3ab5ed292cef8108e937e67bc9e2ccc1ebce
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907882"
---
# <a name="icommandui-interface"></a>ICommandUI インターフェイス

ユーザーインターフェイスコマンドを管理します。

## <a name="syntax"></a>構文

```
interface class ICommandUI
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[icommandui__Check](#check)|このコマンドのユーザーインターフェイス項目を適切なチェック状態に設定します。|
|[ICommandUI::ContinueRouting](#continuerouting)|は、現在のメッセージのルーティングをハンドラーのチェーンの下位にルーティングするようにコマンドルーティング機構に指示します。|
|[ICommandUI::Enabled](#enabled)|このコマンドのユーザーインターフェイス項目を有効または無効にします。|
|[ICommandUI::ID](#id)|`ICommandUI`オブジェクトによって表されるユーザーインターフェイスオブジェクトの ID を取得します。|
|[ICommandUI::Index](#index)|`ICommandUI`オブジェクトによって表されるユーザーインターフェイスオブジェクトのインデックスを取得します。|
|[ICommandUI::Radio](#radio)|このコマンドのユーザーインターフェイス項目を適切なチェック状態に設定します。|
|[ICommandUI::Text](#text)|このコマンドのユーザーインターフェイス項目のテキストを設定します。|

## <a name="remarks"></a>Remarks

このインターフェイスは、ユーザーインターフェイスコマンドを管理するメソッドとプロパティを提供します。 `ICommandUI`は、.net コンポーネントと相互運用する`ICommandUI` MFC アプリケーションで使用される点を除いて、 [CCmdUI クラス](../../mfc/reference/ccmdui-class.md)に似ています。

`ICommandUI`は、 [ICommandTarget](../../mfc/reference/icommandtarget-interface.md)派生クラスの ON_UPDATE_COMMAND_UI ハンドラー内で使用されます。 アプリケーションのユーザーがメニューをアクティブ化 (選択またはクリック) すると、各メニュー項目が [有効] または [無効] と表示されます。 各メニューコマンドのターゲットは、ON_UPDATE_COMMAND_UI ハンドラーを実装することによってこの情報を提供します。 アプリケーション内のコマンドユーザーインターフェイスオブジェクトごとに、[クラスウィザード](mfc-class-wizard.md)を使用して、各ハンドラーのメッセージマップエントリと関数プロトタイプを作成します。

コマンドルーティングでのインターフェイスの`ICommandUI`使用方法の詳細については[、「」を参照してください。Windows フォームコントロール](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)にコマンドルーティングを追加します。

Windows フォームの使用方法の詳細については、「 [MFC での Windows フォームユーザーコントロールの使用](../../dotnet/using-a-windows-form-user-control-in-mfc.md)」を参照してください。

MFC でのユーザーインターフェイスコマンドの管理方法の詳細については、「 [CCmdUI クラス](../../mfc/reference/ccmdui-class.md)」を参照してください。

## <a name="check"></a>ICommandUI:: Check

このコマンドのユーザーインターフェイス項目を適切なチェック状態に設定します。
```
property UICheckState Check;
```

## <a name="remarks"></a>Remarks

このプロパティは、このコマンドのユーザーインターフェイス項目を適切なチェック状態に設定します。 Check を次の値に設定します。
- 0をオフにする
- 1チェック
- 2設定不確定

## <a name="continuerouting"></a> ICommandUI::ContinueRouting

は、現在のメッセージのルーティングをハンドラーのチェーンの下位方向にルーティングするようにコマンドルーティング機構に指示します。
```
void ContinueRouting();
```

## <a name="remarks"></a>Remarks

これは、FALSE を返す ON_COMMAND_EX ハンドラーと組み合わせて使用する必要がある高度なメンバー関数です。 詳細については、「テクニカルノートテクニカルノート 6:メッセージマップ。

## <a name="enabled"></a> ICommandUI::Enabled

このコマンドのユーザーインターフェイス項目を有効または無効にします。
```
property bool Enabled;
```

## <a name="remarks"></a>Remarks

このプロパティは、このコマンドのユーザーインターフェイス項目を有効または無効にします。 項目を有効にする場合は TRUE に、無効にする場合は FALSE に設定します。

## <a name="id"></a> ICommandUI::ID

ICommandUI オブジェクトによって表されるユーザーインターフェイスオブジェクトの ID を取得します。
```
property unsigned int ID;
```

## <a name="remarks"></a>Remarks

このプロパティは、メニュー項目、ツールバーボタン、または ICommandUI オブジェクトによって表されるその他のユーザーインターフェイスオブジェクトの ID (ハンドル) を取得します。

## <a name="index"></a> ICommandUI::Index

ICommandUI オブジェクトによって表されるユーザーインターフェイスオブジェクトのインデックスを取得します。
```
property unsigned int Index;
```

## <a name="remarks"></a>Remarks

このプロパティは、メニュー項目、ツールバーボタン、または ICommandUI オブジェクトによって表されるその他のユーザーインターフェイスオブジェクトのインデックス (ハンドル) を取得します。

## <a name="radio"></a> ICommandUI::Radio

このコマンドのユーザーインターフェイス項目を適切なチェック状態に設定します。
```
property bool Radio;
```

## <a name="remarks"></a>Remarks

このプロパティは、このコマンドのユーザーインターフェイス項目を適切なチェック状態に設定します。 項目を有効にするには、[ラジオ] を [TRUE] に設定します。それ以外の場合は FALSE。

## <a name="text"></a>ICommandUI:: Text

このコマンドのユーザーインターフェイス項目のテキストを設定します。
```
property String^ Text;
```

## <a name="remarks"></a>Remarks

このプロパティは、このコマンドのユーザーインターフェイス項目のテキストを設定します。 テキストをテキスト文字列ハンドルに設定します。

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwinforms (アセンブリに定義されています) (アセンブリに定義されています。

## <a name="see-also"></a>関連項目

[CCmdUI クラス](../../mfc/reference/ccmdui-class.md)
