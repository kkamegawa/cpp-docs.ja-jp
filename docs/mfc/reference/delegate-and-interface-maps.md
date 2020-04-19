---
title: デリゲートとインターフェイス マップ マクロ (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: 8f48b916f7130551fc8d4da5bb2ebc75d8d728d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322983"
---
# <a name="delegate-and-interface-map-macros"></a>デリゲートとインターフェイス マップ マクロ

MFC では、デリゲートとインターフェイス マップをこれらのマクロをサポートします。

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|デリゲートのマップを開始します。|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|コネクション マップの定義を開始します。|
|[CommandHandler デリゲート](#commandhandler)|コマンド ソースは、コールバック メソッドを登録します。  |
|[END_DELEGATE_MAP](#end_delegate_map)|デリゲートのマップを終了します。|
|[END_INTERFACE_MAP](#end_interface_map)|実装ファイルのインターフェイス マップを終了します。 |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|デリゲートのマップ エントリを作成します。|
|[INTERFACE_PART](#interface_part)|BEGIN_INTERFACE_MAP マクロと END_INTERFACE_MAP マクロの間オブジェクトでサポートされる各インターフェイスに使用します。|
|[MAKE_DELEGATE](#make_delegate)|マネージ コントロールをイベント ハンドラーをアタッチします。|

## <a name="begin_delegate_map"></a> BEGIN_DELEGATE_MAP

デリゲートのマップを開始します。

### <a name="syntax"></a>構文

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
マネージ コントロールがホストされているクラスです。

### <a name="remarks"></a>Remarks

このマクロは、デリゲートのマップを構成するデリゲートのエントリの一覧の先頭をマークします。 このマクロの使用方法の例は、次を参照してください。 [EVENT_DELEGATE_ENTRY](#event_delegate_entry)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** msclr\event.h

##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

実装ファイルで使用すると、コネクション マップの定義を開始します。

### <a name="syntax"></a>構文

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
定義するインターフェイス マップが含まれるクラス

*baseClass*<br/>
元のクラス*クラス*から派生します。

### <a name="remarks"></a>Remarks

実装するインターフェイスごとに、INTERFACE_PART マクロの呼び出しがあります。 クラスを使用する集約ごとに、1 つの INTERFACE_AGGREGATE マクロ呼び出しがあります。

インターフェイス マップの詳細については、次を参照してください。[テクニカル ノート 38](../tn038-mfc-ole-iunknown-implementation.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="commandhandler"></a>CommandHandler デリゲート

コマンド ソースは、コールバック メソッドを登録します。

### <a name="syntax"></a>構文

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>パラメーター

*cmdID*<br/>
コマンド ID。

### <a name="remarks"></a>Remarks

このデリゲートは、コマンド ソース、コールバック メソッドを登録します。 コマンド ソース オブジェクトにデリゲートを追加すると、コールバック メソッドには、指定したソースからのコマンドのハンドラーになります。

詳細については、「[方法 :コマンドの追加フォーム コントロールを Windows へのルーティング](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)します。

Windows フォームの使用に関する詳細については、次を参照してください。 [MFC における Windows フォーム ユーザー コントロールを使用して](../../dotnet/using-a-windows-form-user-control-in-mfc.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwinforms.h (アセンブリ atlmfc\lib\mfcmifc80.dll で定義)

##  <a name="commanduihandler"></a>CommandUIHandler

ユーザー インターフェイス更新コマンドのメッセージをコールバック メソッドを登録します。

### <a name="syntax"></a>構文

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>パラメーター

*cmdID*<br/>
コマンド ID。

*cmdUI*<br/>
コマンド メッセージ id。

### <a name="remarks"></a>Remarks

このデリゲートは、ユーザー インターフェイスの更新コマンド メッセージでコールバック メソッドを登録します。 `CommandUIHandler` ような[CommandHandler](#commandhandler)する点を除いて、このデリゲートは、ユーザー インターフェイス オブジェクトの update コマンドを使用します。 ユーザー インターフェイスの更新コマンド メッセージ ハンドラーのメソッドが一対一マップされた必要があります。

Windows フォームの使用に関する詳細については、次を参照してください。 [MFC における Windows フォーム ユーザー コントロールを使用して](../../dotnet/using-a-windows-form-user-control-in-mfc.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwinforms.h (アセンブリ atlmfc\lib\mfcmifc80.dll で定義)

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP

デリゲートのマップを終了します。

### <a name="syntax"></a>構文

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Remarks

このマクロは、デリゲートのマップを構成するデリゲートのエントリの一覧の末尾をマークします。 このマクロの使用方法の例は、次を参照してください。 [EVENT_DELEGATE_ENTRY](#event_delegate_entry)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** msclr\event.h

##  <a name="end_interface_map"></a>END_INTERFACE_MAP

実装ファイルのインターフェイス マップを終了します。

### <a name="syntax"></a>構文

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Remarks

インターフェイス マップの詳細については、次を参照してください。[テクニカル ノート 38](../tn038-mfc-ole-iunknown-implementation.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

デリゲートのマップ エントリを作成します。

### <a name="syntax"></a>構文

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>パラメーター

*メンバー*<br/>
コントロールに接続するイベント ハンドラー メソッド。

*ARG0*<br/>
管理対象のイベント ハンドラー メソッドの最初の引数など`Object^`します。

*ARG1*<br/>
管理対象のイベント ハンドラー メソッドの 2 番目の引数など`EventArgs^`します。

### <a name="remarks"></a>Remarks

デリゲートのマップ内の各エントリがによって作成された管理対象のイベント ハンドラー デリゲートに対応[MAKE_DELEGATE](#make_delegate)します。

### <a name="example"></a>例

次のコード例は、EVENT_DELEGATE_ENTRY を使用して、デリゲートのマップのエントリを作成する方法を示しています、`OnClick`イベント ハンドラー。 また MAKE_DELEGATE のコード例を参照してください。 詳細については、「[方法 :ネイティブ C++ クラスから Windows フォーム イベントをシンク](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)します。

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>必要条件

**ヘッダー:** msclr\event.h

##  <a name="interface_part"></a>INTERFACE_PART

BEGIN_INTERFACE_MAP マクロと END_INTERFACE_MAP マクロの間オブジェクトでサポートされる各インターフェイスに使用します。

### <a name="syntax"></a>構文

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
インターフェイス マップを持つクラスの名前。
*iid*<br/>
埋め込みクラスにマップする IID。
*マクロ*<br/>
ローカル クラスの名前。

### <a name="remarks"></a>Remarks

示されたクラスのメンバーに IID をマップできます*クラス*と*マクロ*します。

インターフェイス マップの詳細については、次を参照してください。[テクニカル ノート 38](../tn038-mfc-ole-iunknown-implementation.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="make_delegate"></a>MAKE_DELEGATE

マネージ コントロールをイベント ハンドラーをアタッチします。

### <a name="syntax"></a>構文

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>パラメーター

*DELEGATE*<br/>
管理対象のイベント ハンドラーの型を委任するよう[EventHandler](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True)します。

*メンバー*<br/>
コントロールに接続するイベント ハンドラー メソッドの名前。

### <a name="remarks"></a>Remarks

このマクロは、型のマネージ イベント ハンドラー デリゲートを作成します。*委任*と名前の*メンバー*します。 管理対象のイベント ハンドラーのデリゲートには、管理対象のイベントを処理するネイティブ クラスができます。

### <a name="example"></a>例

次のコード例は、呼び出す方法を示しています。`MAKE_DELEGATE`をアタッチする、 `OnClick` MFC コントロールにイベント ハンドラーを`MyControl`します。 MFC アプリケーションでこのマクロのしくみの広範な説明については、次を参照してください。[方法。ネイティブ C++ クラスから Windows フォーム イベントをシンク](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)します。

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>必要条件

**ヘッダー:** msclr\event.h

## <a name="see-also"></a>関連項目

[方法: ネイティブ C++ クラスから Windows フォーム イベントをシンクする](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[方法: Windows フォーム コントロールにコマンド ルーティングを追加する](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[マクロとグローバル](mfc-macros-and-globals.md)<br/>
