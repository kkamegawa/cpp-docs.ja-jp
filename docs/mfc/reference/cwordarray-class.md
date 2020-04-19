---
title: CWordArray クラス
ms.date: 09/07/2019
f1_keywords:
- CWordArray
- AFXCOLL/CWordArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 2ba2c194-2c6c-40ff-9db4-e9dbe57e1f57
ms.openlocfilehash: c136bbb14e0d7cffc604813731b6f87ba18063cf
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907909"
---
# <a name="cwordarray-class"></a>CWordArray クラス

16 ビットのワードの配列をサポートします。

## <a name="syntax"></a>構文

```
class CWordArray : public CObject
```

## <a name="members"></a>メンバー

の`CWordArray`メンバー関数は、 [CObArray](../../mfc/reference/cobarray-class.md)クラスのメンバー関数に似ています。 メンバー関数については `CObArray` クラスの説明を参照してください。 関数パラメーターまたは戻り値として[CObject](../../mfc/reference/cobject-class.md)ポインターが表示されている場合は、単語を代わりに使用します。

`CObject* CObArray::GetAt( int <nIndex> ) const;`

たとえば、次のように変換します。

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CObArray:: CObArray](../../mfc/reference/cobarray-class.md#cobarray)|空の配列を生成します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|配列の末尾に要素を追加します。必要に応じて、配列を大きくします。|
|[CObArray:: Append](../../mfc/reference/cobarray-class.md#append)|配列に別の配列を追加します。必要に応じて、配列を大きくします。|
|[CObArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|配列に別の配列をコピーします。必要に応じて、配列を大きくします。|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|配列内の要素ポインターへの一時的な参照を返します。|
|[CObArray:: FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|現在の上限を超えている未使用のメモリをすべて解放します。|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|指定されたインデックス位置にある値を返します。|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|この配列内の要素の数を取得します。|
|[CObArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|配列内の要素へのアクセスを許可します。 NULL を指定できます。|
|[CObArray:: GetSize](../../mfc/reference/cobarray-class.md#getsize)|この配列内の要素の数を取得します。|
|[CObArray:: System.array.getupperbound](../../mfc/reference/cobarray-class.md#getupperbound)|有効な最大のインデックスを返します。|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|指定されたインデックス位置に要素 (または別の配列内のすべての要素) を挿入します。|
|[CObArray:: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|配列が空かどうかを判別します。|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|この配列からすべての要素を削除します。|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|特定のインデックス位置にある要素を削除します。|
|[CObArray:: SetAt](../../mfc/reference/cobarray-class.md#setat)|指定されたインデックスの値を設定します。配列は大きくできません。|
|[CObArray:: SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|指定されたインデックスの値を設定します。必要に応じて、配列を大きくします。|
|[CObArray:: SetSize](../../mfc/reference/cobarray-class.md#setsize)|この配列に含まれる要素の数を設定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CObArray:: operator&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|指定されたインデックス位置にある要素を設定または取得します。|

## <a name="remarks"></a>Remarks

`CWordArray`には、要素のシリアル化とダンプをサポートする[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)マクロが組み込まれています。 オーバーロードされた挿入演算子または[CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize)メンバー関数を使用して、単語の配列がアーカイブに格納されている場合は、各要素がシリアル化されます。

> [!NOTE]
>  配列を使用する前に、`SetSize` を使用してそのサイズを設定し、メモリを割り当てます。 `SetSize` を使用しない場合、配列に要素を追加すると、配列の再割り当てとコピーが頻繁に発生します。 頻繁な再割り当てとコピーは非効率であり、メモリが断片化される可能性があります。

配列内の個々の要素のダンプが必要な場合は、ダンプコンテキストの深さを1以上に設定する必要があります。

の使用方法`CWordArray`の詳細については、「[コレクション](../../mfc/collections.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcoll.h

##  <a name="icommandsource_interface"></a>ICommandSource インターフェイス

コマンドソースオブジェクトからユーザーコントロールに送信されたコマンドを管理します。

```
interface class ICommandSource
```

### <a name="remarks"></a>Remarks

MFC ビューでユーザーコントロールをホストする場合、 [CWinFormsView クラス](../../mfc/reference/cwinformsview-class.md)は、コマンドをルーティングし、コマンド UI メッセージをユーザーコントロールに更新して、mfc コマンドを処理できるようにします (たとえば、フレームメニュー項目やツールバーボタンなど)。 を実装することにより、ユーザーコントロールに`ICommandSource`オブジェクトへの参照を提供します。

「[方法:の使用](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) `ICommandTarget`方法の例については、Windows フォームコントロールにコマンドルーティングを追加します。

Windows フォームの使用方法の詳細については、「 [MFC での Windows フォームユーザーコントロールの使用](../../dotnet/using-a-windows-form-user-control-in-mfc.md)」を参照してください。

##  <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler

コマンドソースオブジェクトにコマンドハンドラーを追加します。

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>パラメーター

*cmdID*<br/>
コマンド ID。

*cmdHandler*<br/>
コマンドハンドラーメソッドへのハンドル。

### <a name="remarks"></a>Remarks

このメソッドは、コマンドハンドラーの*Cmdhandler*をコマンドソースオブジェクトに追加し、ハンドラーを*cmdID*にマップします。

「[方法:の使用](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) `AddCommandHandler`方法の例については、Windows フォームコントロールにコマンドルーティングを追加します。

##  <a name="addcommandrangehandler"></a>  ICommandSource::AddCommandRangeHandler

コマンドソースオブジェクトにコマンドハンドラーのグループを追加します。

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>パラメーター

*cmdIDMin*<br/>
コマンド ID 範囲の開始インデックス。

*cmdIDMax*<br/>
コマンド ID 範囲の終了インデックス。

*cmdHandler*<br/>
コマンドのマップ先となるメッセージハンドラーメソッドへのハンドル。

### <a name="remarks"></a>Remarks

このメソッドは、連続した一連のコマンド Id を1つのメッセージハンドラーにマップして、コマンドソースオブジェクトに追加します。 これは、関連するボタンのグループを1つの方法で処理するために使用されます。

##  <a name="addcommandrangeuihandler"></a>  ICommandSource::AddCommandRangeUIHandler

コマンドソースオブジェクトに、ユーザーインターフェイスのコマンドメッセージハンドラーのグループを追加します。

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>パラメーター

*cmdIDMin*<br/>
コマンド ID 範囲の開始インデックス。

*cmdIDMax*<br/>
コマンド ID 範囲の終了インデックス。

*cmdHandler*<br/>
コマンドのマップ先となるメッセージハンドラーメソッドへのハンドル。

### <a name="remarks"></a>Remarks

このメソッドは、コマンド Id の連続した範囲を1つのユーザーインターフェイスのコマンドメッセージハンドラーにマップして、コマンドソースオブジェクトに追加します。 これは、関連するボタンのグループを1つの方法で処理するために使用されます。

##  <a name="addcommanduihandler"></a>  ICommandSource::AddCommandUIHandler

コマンドソースオブジェクトにユーザーインターフェイスのコマンドメッセージハンドラーを追加します。

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>パラメーター

*cmdID*<br/>
コマンド ID。

*cmdUIHandler*<br/>
ユーザーインターフェイスコマンドメッセージハンドラーメソッドへのハンドル。

### <a name="remarks"></a>Remarks

このメソッドは、コマンドソースオブジェクトにユーザーインターフェイスのコマンドメッセージハンドラー *Cmdhandler*を追加し、そのハンドラーを*cmdID*にマップします。

##  <a name="postcommand"></a>  ICommandSource::PostCommand

処理されるのを待たずにメッセージをポストします。

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>パラメーター

*command*<br/>
ポストされるメッセージのコマンド ID。

### <a name="remarks"></a>Remarks

このメソッドは、*コマンド*で指定された ID にマップされたメッセージを非同期にポストします。 [CWnd::P ostMessage](../../mfc/reference/cwnd-class.md#postmessage)を呼び出して、ウィンドウのメッセージキューにメッセージを配置し、対応するウィンドウがメッセージを処理するのを待たずに制御を戻します。

##  <a name="removecommandhandler"></a>  ICommandSource::RemoveCommandHandler

コマンドソースオブジェクトからコマンドハンドラーを削除します。

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>パラメーター

*cmdID*<br/>
コマンド ID。

### <a name="remarks"></a>Remarks

このメソッドは、コマンドソースオブジェクトから、 *cmdID*にマップされたコマンドハンドラーを削除します。

##  <a name="removecommandrangehandler"></a>  ICommandSource::RemoveCommandRangeHandler

コマンドソースオブジェクトからコマンドハンドラーのグループを削除します。

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>パラメーター

*cmdIDMin*<br/>
コマンド ID 範囲の開始インデックス。

*cmdIDMax*<br/>
コマンド ID 範囲の終了インデックス。

### <a name="remarks"></a>Remarks

このメソッドは、 *cmdIDMin*および*cmdIDMax*によって指定されたコマンド id にマップされたメッセージハンドラーのグループを、コマンドソースオブジェクトから削除します。

##  <a name="removecommandrangeuihandler"></a>  ICommandSource::RemoveCommandRangeUIHandler

コマンドソースオブジェクトからユーザーインターフェイスのコマンドメッセージハンドラーのグループを削除します。

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>パラメーター

*cmdIDMin*<br/>
コマンド ID 範囲の開始インデックス。

*cmdIDMax*<br/>
コマンド ID 範囲の終了インデックス。

### <a name="remarks"></a>Remarks

このメソッドは、コマンドソースオブジェクトから、 *cmdIDMin*および*cmdIDMax*によって指定されたコマンド id にマップされた、ユーザーインターフェイスのコマンドメッセージハンドラーのグループを削除します。

##  <a name="removecommanduihandler"></a>  ICommandSource::RemoveCommandUIHandler

コマンドソースオブジェクトからユーザーインターフェイスのコマンドメッセージハンドラーを削除します。

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>パラメーター

*cmdID*<br/>
コマンド ID。

### <a name="remarks"></a>Remarks

このメソッドは、コマンドソースオブジェクトから、 *cmdID*にマップされたユーザーインターフェイスのコマンドメッセージハンドラーを削除します。

##  <a name="sendcommand"></a>  ICommandSource::SendCommand

メッセージを送信し、が返される前に処理されるのを待機します。

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>パラメーター

*command*<br/>
送信されるメッセージのコマンド ID。

### <a name="remarks"></a>Remarks

このメソッドは、*コマンド*で指定された ID にマップされたメッセージを同期的に送信します。 [CWnd:: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage)を呼び出して、メッセージをウィンドウのメッセージキューに配置し、ウィンドウプロシージャがメッセージを処理してから制御が戻るまで待機します。

##  <a name="icommandtarget_interface"></a>ICommandTarget インターフェイス

コマンドソースオブジェクトからコマンドを受信するためのインターフェイスをユーザーコントロールに提供します。

```
interface class ICommandTarget
```

### <a name="remarks"></a>Remarks

MFC ビューでユーザーコントロールをホストすると、 [CWinFormsView](../../mfc/reference/cwinformsview-class.md)はコマンドをルーティングし、コマンド UI メッセージをユーザーコントロールに送信して、mfc コマンドを処理できるようにします (たとえば、フレームのメニュー項目やツールバーのボタンなど)。 を実装`ICommandTarget`することにより、ユーザーコントロールにオブジェクトへの参照を提供します。

「[方法:の使用](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) `ICommandTarget`方法の例については、Windows フォームコントロールにコマンドルーティングを追加します。

Windows フォームの使用方法の詳細については、「 [MFC での Windows フォームユーザーコントロールの使用](../../dotnet/using-a-windows-form-user-control-in-mfc.md)」を参照してください。

##  <a name="initialize"></a>ICommandTarget:: Initialize

コマンドターゲットオブジェクトを初期化します。

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>パラメーター

*cmdSource*<br/>
コマンドソースオブジェクトへのハンドル。

### <a name="remarks"></a>Remarks

MFC ビューでユーザーコントロールをホストすると、 [CWinFormsView](../../mfc/reference/cwinformsview-class.md)はコマンドをルーティングし、ユーザーコントロールにコマンド UI メッセージを更新して、mfc コマンドを処理できるようにします。

このメソッドは、コマンドターゲットオブジェクトを初期化し、指定したコマンドソースオブジェクト*Cmdsource*に関連付けます。 これは、ユーザーコントロールクラスの実装で呼び出される必要があります。 初期化時には、 `Initialize`実装で[ICommandSource:: addcommandhandler](../../mfc/reference/icommandsource-interface.md)を呼び出すことによって、コマンドハンドラーをコマンドソースオブジェクトに登録する必要があります。 「[方法:を使用](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) `Initialize`してこれを行う方法の例については、Windows フォームコントロールにコマンドルーティングを追加します。

##  <a name="icommandui_interface"></a>ICommandUI インターフェイス

ユーザーインターフェイスコマンドを管理します。

```
interface class ICommandUI
```

### <a name="remarks"></a>Remarks

このインターフェイスは、ユーザーインターフェイスコマンドを管理するメソッドとプロパティを提供します。 `ICommandUI`は、.net コンポーネントと相互運用する`ICommandUI` MFC アプリケーションで使用される点を除いて、 [CCmdUI クラス](../../mfc/reference/ccmdui-class.md)に似ています。

`ICommandUI`は、派生クラス`ON_UPDATE_COMMAND_UI`のハンドラー内で使用されます。 アプリケーションのユーザーがメニューをアクティブ化 (選択またはクリック) すると、各メニュー項目が [有効] または [無効] と表示されます。 各メニューコマンドのターゲットは、 `ON_UPDATE_COMMAND_UI`ハンドラーを実装することによってこの情報を提供します。 アプリケーション内のコマンドユーザーインターフェイスオブジェクトごとに、[クラスウィザード](mfc-class-wizard.md)または**プロパティ**ウィンドウ (**クラスビュー**) を使用して、各ハンドラーのメッセージマップエントリと関数プロトタイプを作成します。

コマンドルーティングでのインターフェイスの`ICommandUI`使用方法の詳細については[、「」を参照してください。Windows フォームコントロール](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)にコマンドルーティングを追加します。

Windows フォームの使用方法の詳細については、「 [MFC での Windows フォームユーザーコントロールの使用](../../dotnet/using-a-windows-form-user-control-in-mfc.md)」を参照してください。

MFC でのユーザーインターフェイスコマンドの管理方法の詳細については、「 [CCmdUI クラス](../../mfc/reference/ccmdui-class.md)」を参照してください。

##  <a name="check"></a>  ICommandUI::Check

このコマンドのユーザーインターフェイス項目を適切なチェック状態に設定します。

```
property UICheckState Check;
```

### <a name="remarks"></a>Remarks

このプロパティは、このコマンドのユーザーインターフェイス項目を適切なチェック状態に設定します。 次`Check`の値に設定します。

|用語|定義|
|----------|----------------|
|0|外し|
|1|チェック|
|2|不確定の設定|

##  <a name="continuerouting"></a>  ICommandUI::ContinueRouting

は、現在のメッセージのルーティングをハンドラーのチェーンの下位方向にルーティングするようにコマンドルーティング機構に指示します。

```
void ContinueRouting();
```

### <a name="remarks"></a>Remarks

これは、FALSE を返す[ON_COMMAND_EX](message-map-macros-mfc.md#on_command_ex)ハンドラーと組み合わせて使用する必要がある高度なメンバー関数です。 詳細については、「 [テクニカルノートテクニカルノート 6:メッセージマップ](../../mfc/tn006-message-maps.md)。

##  <a name="enabled"></a>  ICommandUI::Enabled

このコマンドのユーザーインターフェイス項目を有効または無効にします。

```
property bool Enabled;
```

### <a name="remarks"></a>Remarks

このプロパティは、このコマンドのユーザーインターフェイス項目を有効または無効にします。 項目`Enabled`を有効にする場合は TRUE に設定し、無効にする場合は FALSE に設定します。

##  <a name="id"></a>  ICommandUI::ID

`ICommandUI`オブジェクトによって表されるユーザーインターフェイスオブジェクトの ID を取得します。

```
property unsigned int ID;
```

### <a name="remarks"></a>Remarks

このプロパティは、メニュー項目、ツールバーボタン、または`ICommandUI`オブジェクトによって表されるその他のユーザーインターフェイスオブジェクトの ID (ハンドル) を取得します。

##  <a name="index"></a>  ICommandUI::Index

`ICommandUI`オブジェクトによって表されるユーザーインターフェイスオブジェクトのインデックスを取得します。

```
property unsigned int Index;
```

### <a name="remarks"></a>Remarks

このプロパティは、メニュー項目、ツールバーボタン、または`ICommandUI`オブジェクトによって表されるその他のユーザーインターフェイスオブジェクトのインデックス (ハンドル) を取得します。

##  <a name="radio"></a>  ICommandUI::Radio

このコマンドのユーザーインターフェイス項目を適切なチェック状態に設定します。

```
property bool Radio;
```

### <a name="remarks"></a>Remarks

このプロパティは、このコマンドのユーザーインターフェイス項目を適切なチェック状態に設定します。 項目`Radio`を有効にする場合は TRUE に設定します。それ以外の場合は FALSE に設定します。

##  <a name="text"></a>  ICommandUI::Text

このコマンドのユーザーインターフェイス項目のテキストを設定します。

```
property String^ Text;
```

### <a name="remarks"></a>Remarks

このプロパティは、このコマンドのユーザーインターフェイス項目のテキストを設定します。 を`Text`テキスト文字列ハンドルに設定します。

##  <a name="iview_interface"></a>IView インターフェイス

[CWinFormsView](../../mfc/reference/cwinformsview-class.md)が、ビュー通知をマネージコントロールに送信するために使用するいくつかのメソッドを実装します。

```
interface class IView
```

### <a name="remarks"></a>Remarks

`IView`は、を使用`CWinFormsView`して、共通のビュー通知をホスト型マネージコントロールに転送するいくつかのメソッドを実装します。 これらは、 [OnInitialUpdate](../../mfc/reference/iview-interface.md)、 [OnUpdate](../../mfc/reference/iview-interface.md) 、および[onアクティブビュー](../../mfc/reference/iview-interface.md)です。

`IView`は[CView](../../mfc/reference/cview-class.md)に似ていますが、はマネージビューおよびコントロールでのみ使用されます。

Windows フォームの使用方法の詳細については、「 [MFC での Windows フォームユーザーコントロールの使用](../../dotnet/using-a-windows-form-user-control-in-mfc.md)」を参照してください。

##  <a name="onactivateview"></a>  IView::OnActivateView

ビューがアクティブ化または非アクティブ化されたときに MFC によって呼び出されます。

```
void OnActivateView(bool activate);
```

### <a name="parameters"></a>パラメーター

*する*<br/>
ビューがアクティブ化または非アクティブ化されているかどうかを示します。

##  <a name="oninitialupdate"></a>  IView::OnInitialUpdate

最初にビューがドキュメントにアタッチされた後、最初にビューが表示される前に、フレームワークによって呼び出されます。

```
void OnInitialUpdate();
```

##  <a name="onupdate"></a>IView:: OnUpdate

ビューのドキュメントが変更された後に、MFC によって呼び出されます。

```
void OnUpdate();
```

### <a name="remarks"></a>Remarks

この関数を使用すると、ビューが変更を反映するように表示を更新できます。

## <a name="see-also"></a>関連項目

[MFC サンプル収集](../../overview/visual-cpp-samples.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
