---
title: CRecordView クラス
ms.date: 11/04/2016
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
ms.openlocfilehash: 409739d97c9f7ae9a730ac8f05bd86e647da2c71
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215532"
---
# <a name="crecordview-class"></a>CRecordView クラス

コントロール内にデータベース レコードを表示するビューです。

## <a name="syntax"></a>構文

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|Name|説明|
|----------|-----------------|
|[CRecordView:: CRecordView](#crecordview)|`CRecordView` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[CRecordView:: IsOnFirstRecord](#isonfirstrecord)|現在のレコードが、関連付けられたレコードセット内の最初のレコードの場合は、0以外の値を返します。|
|[CRecordView:: IsOnLastRecord](#isonlastrecord)|現在のレコードが、関連付けられたレコードセットの最後のレコードである場合は、0以外の値を返します。|
|[CRecordView:: OnGetRecordset](#ongetrecordset)|`CRecordset`から派生したクラスのオブジェクトへのポインターを返します。 ClassWizard はこの関数をオーバーライドし、必要に応じてレコードセットを作成します。|
|[CRecordView:: OnMove](#onmove)||

### <a name="protected-methods"></a>プロテクト メソッド

|Name|説明|
|----------|-----------------|
|[CRecordView:: OnMove](#onmove)|現在のレコードが変更されている場合、はデータソースでそのレコードを更新してから、指定されたレコード (next、previous、first、last) に移動します。|

## <a name="remarks"></a>コメント

ビューは、`CRecordset` オブジェクトに直接接続されたフォームビューです。 ダイアログテンプレートリソースからビューが作成され、ダイアログテンプレートのコントロールに `CRecordset` オブジェクトのフィールドが表示されます。 `CRecordView` オブジェクトは、ダイアログデータエクスチェンジ (DDX) とレコードフィールドエクスチェンジ (RFX) を使用して、フォーム上のコントロールとレコードセットのフィールドとの間のデータの移動を自動化します。 また `CRecordView` は、最初、次、前、または最後のレコードに移動するための既定の実装と、現在表示されているレコードを更新するためのインターフェイスも提供します。

> [!NOTE]
>  Open Database Connectivity (ODBC) クラスではなく、データアクセスオブジェクト (DAO) クラスを使用している場合は、代わりにクラス[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)を使用します。 詳細については、記事「[概要: データベースプログラミング](../../data/data-access-programming-mfc-atl.md)」を参照してください。

レコードビューを作成する最も一般的な方法は、アプリケーションウィザードを使用することです。 アプリケーションウィザードでは、レコードビュークラスとそれに関連付けられているレコードセットクラスの両方がスケルトンスターターアプリケーションの一部として作成されます。 アプリケーションウィザードでレコードビュークラスを作成しない場合は、後で ClassWizard を使用して作成できます。 単に1つのフォームが必要な場合は、アプリケーションウィザードのアプローチが簡単です。 ClassWizard では、開発プロセスの後半でレコードビューを使用することを決定できます。 ClassWizard を使用してレコードビューとレコードセットを個別に作成し、それを接続することは、レコードセットクラスとそのの名前付けをより細かく制御できるため、最も柔軟な方法です。H/。CPP ファイル。 この方法では、同じレコードセットクラスに複数のレコードビューを含めることもできます。

エンドユーザーがレコードビューでレコード間を簡単に移動できるようにするために、アプリケーションウィザードでは、最初、次、前、または最後のレコードに移動するためのメニュー (および必要に応じてツールバー) リソースを作成します。 ClassWizard でレコードビュークラスを作成する場合は、メニューエディターとビットマップエディターを使用してこれらのリソースを自分で作成する必要があります。

レコード間の移動の既定の実装の詳細については、「`IsOnFirstRecord` と `IsOnLastRecord`」と「[レコードビューを使用し](../../data/using-a-record-view-mfc-data-access.md)たアーティクル」を参照してください。

レコードビューでユーザーインターフェイスを更新できるように、`CRecordView` はレコードセット内のユーザーの位置を追跡します。 ユーザーがレコードセットの末尾に移動すると、[レコード] ビューでは、メニュー項目やツールバーボタンなどのユーザーインターフェイスオブジェクトが、同じ方向に移動するために無効になります。

レコードビューおよびレコードセットクラスの宣言と使用の詳細については、 [「レコードビュー](../../data/record-views-mfc-data-access.md)のデザインと作成」の「レコードビューのデザインと作成」を参照してください。 レコードビューの動作と使用方法の詳細については、[レコードビューの使用](../../data/using-a-record-view-mfc-data-access.md)に関する記事を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[から派生しているのではない](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>要件

**ヘッダー:** afxdb.h

##  <a name="crecordview"></a>CRecordView:: CRecordView

`CRecordView`から派生した型のオブジェクトを作成する場合は、コンストラクターのいずれかの形式を呼び出して、ビューオブジェクトを初期化し、ビューの基になるダイアログリソースを識別します。

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>パラメーター

*lpszTemplateName*<br/>
ダイアログテンプレートリソースの名前である null で終わる文字列を格納します。

*nIDTemplate*<br/>
ダイアログテンプレートリソースの ID 番号を格納します。

### <a name="remarks"></a>コメント

リソースを名前で識別する (コンストラクターの引数として文字列を渡す) か、ID (符号なし整数を引数として渡す) のいずれかを指定できます。 リソース ID を使用することをお勧めします。

> [!NOTE]
>  派生クラスは、独自のコンストラクターを提供*する必要があり*ます。 派生クラスのコンストラクターで、次の例に示すように、リソース名または ID を引数として使用して `CRecordView::CRecordView` コンストラクターを呼び出します。

`CRecordView::OnInitialUpdate` は、`DoDataExchange`を呼び出す `UpdateData`を呼び出します。 この `DoDataExchange` への最初の呼び出しでは、`CRecordView` コントロール (間接的) を、ClassWizard によって作成された `CRecordset` フィールドデータメンバーに接続します。 これらのデータメンバーは、基底クラス `CFormView::OnInitialUpdate` メンバー関数を呼び出すまでは使用できません。

> [!NOTE]
>  ClassWizard を使用する場合、ウィザードは**列挙**値 `CRecordView::IDD`を定義し、クラス宣言で指定して、コンストラクターのメンバー初期化リストで使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

##  <a name="isonfirstrecord"></a>CRecordView:: IsOnFirstRecord

このメンバー関数を呼び出して、現在のレコードが、このレコードビューに関連付けられているレコードセットオブジェクトの最初のレコードであるかどうかを確認します。

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>戻り値

現在のレコードがレコードセット内の最初のレコードである場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>コメント

この関数は、ClassWizard によって作成された既定のコマンド更新ハンドラーの独自の実装を記述する場合に便利です。

ユーザーが最初のレコードに移動した場合、フレームワークは、最初または前のレコードに移動するために必要なユーザーインターフェイスオブジェクトを無効にします。

##  <a name="isonlastrecord"></a>CRecordView:: IsOnLastRecord

このメンバー関数を呼び出して、現在のレコードが、このレコードビューに関連付けられているレコードセットオブジェクトの最後のレコードであるかどうかを確認します。

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>戻り値

現在のレコードがレコードセット内の最後のレコードである場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>コメント

この関数は、ClassWizard によって記述された既定のコマンド更新ハンドラーの実装を作成して、レコードからレコードへ移動するためのユーザーインターフェイスをサポートする場合に役立ちます。

> [!CAUTION]
>  この関数の結果は信頼性が高くなります。ただし、ビューでは、ユーザーがレコードセットを移動してから、レコードセットの末尾を検出することはできません。 ユーザーは最後のレコードを超えて移動する必要があります。これにより、レコードビューでは、次のレコードまたは最後のレコードに移動するためのユーザーインターフェイスオブジェクトを無効にする必要があることがわかります。 ユーザーが最後のレコードを移動してから最後のレコード (またはその前) に戻ると、レコードビューでレコードセット内のユーザーの位置を追跡し、ユーザーインターフェイスオブジェクトを正しく無効にすることができます。 `IsOnLastRecord` は、実装関数を呼び出した後、ID_RECORD_LAST コマンドまたは `CRecordset::MoveLast`を処理する `OnRecordLast`も信頼できません。

##  <a name="ongetrecordset"></a>CRecordView:: OnGetRecordset

レコードビューに関連付けられている `CRecordset`派生オブジェクトへのポインターを返します。

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>戻り値

オブジェクトが正常に作成された場合は、`CRecordset`派生オブジェクトへのポインター。それ以外の場合は NULL ポインター。

### <a name="remarks"></a>コメント

このメンバー関数をオーバーライドして、レコードセットオブジェクトを構築または取得し、そのオブジェクトへのポインターを返すようにする必要があります。 ClassWizard でレコードビュークラスを宣言すると、ウィザードによって既定の上書きが書き込まれます。 ClassWizard の既定の実装では、レコードビューに格納されているレコードセットポインターが存在する場合、そのポインターが返されます。 そうでない場合は、ClassWizard で指定した種類のレコードセットオブジェクトを構築し、その `Open` メンバー関数を呼び出してテーブルを開くかクエリを実行し、オブジェクトへのポインターを返します。

詳細と例については、レコード[ビューの使用](../../data/using-a-record-view-mfc-data-access.md)に関する記事を参照してください。

##  <a name="onmove"></a>CRecordView:: OnMove

レコードセット内の別のレコードに移動し、そのフィールドを [レコード] ビューのコントロールに表示するには、このメンバー関数を呼び出します。

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>パラメーター

*nIDMoveCommand*<br/>
次の標準コマンド ID 値のいずれか。

- ID_RECORD_FIRST レコードセット内の最初のレコードに移動します。

- ID_RECORD_LAST レコードセット内の最後のレコードに移動します。

- ID_RECORD_NEXT レコードセット内の次のレコードに移動します。

- ID_RECORD_PREV レコードセット内の前のレコードに移動します。

### <a name="return-value"></a>戻り値

移動が成功した場合は0以外の。それ以外の場合は、移動要求が拒否された場合は0です。

### <a name="remarks"></a>コメント

既定の実装は、レコードビューに関連付けられている `CRecordset` オブジェクトの適切な `Move` メンバー関数を呼び出します。

既定では、[レコード] ビューでユーザーがデータソースの現在のレコードを変更した場合、`OnMove` はそのレコードを更新します。

アプリケーションウィザードでは、最初のレコード、最後のレコード、次のレコード、および前の [レコード] メニュー項目を含むメニューリソースが作成されます。 [ドッキング可能なツールバー] オプションを選択した場合は、アプリケーションウィザードによって、これらのコマンドに対応するボタンを備えたツールバーも作成されます。

レコードセットの最後のレコードを越えて移動すると、レコードビューでは、最後のレコードが引き続き表示されます。 最初のレコードを後方に移動すると、レコードビューでは、最初のレコードが引き続き表示されます。

> [!CAUTION]
>  レコードセットにレコードがない場合、`OnMove` を呼び出すと例外がスローされます。 対応する移動操作の前に、適切なユーザーインターフェイス更新ハンドラー関数 (`OnUpdateRecordFirst`、`OnUpdateRecordLast`、`OnUpdateRecordNext`、または `OnUpdateRecordPrev`) を呼び出して、レコードセットにレコードがあるかどうかを確認します。

## <a name="see-also"></a>参照

[CFormView クラス](../../mfc/reference/cformview-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)<br/>
[CFormView クラス](../../mfc/reference/cformview-class.md)
