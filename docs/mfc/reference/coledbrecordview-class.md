---
title: COleDBRecordView クラス
ms.date: 11/04/2016
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
ms.openlocfilehash: 1b09599479010f87e396e6f576c9524651923f9f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341718"
---
# <a name="coledbrecordview-class"></a>COleDBRecordView クラス

コントロール内にデータベース レコードを表示するビューです。

## <a name="syntax"></a>構文

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[COleDBRecordView::COleDBRecordView](#coledbrecordview)|`COleDBRecordView` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleDBRecordView::OnGetRowset](#ongetrowset)|標準の HRESULT 値を返します。|
|[COleDBRecordView::OnMove](#onmove)|データ ソース (dirty) の場合、現在のレコードを更新し、指定されたレコードに移動します (次に、前の最初のページまたは最後)。|

## <a name="remarks"></a>Remarks

ビューが、フォーム ビューに直接接続されている、`CRowset`オブジェクト。 ビューはダイアログ テンプレート リソースから作成されのフィールドが表示されます、`CRowset`ダイアログ テンプレートのコントロール内のオブジェクト。 `COleDBRecordView`オブジェクトは、ダイアログ データ エクス チェンジ (DDX) を使用し、ナビゲーションの機能に組み込まれて`CRowset`フォーム上のコントロールと、行セットのフィールド間のデータ移動を自動化します。 `COleDBRecordView` 移動するための既定の実装を提供、最初に [次へ]、前、または最後のレコードとインターフェイス ビューで現在のレコードを更新します。

DDX 関数を使用する`COleDbRecordView`をデータベースのレコード セットから直接データを取得し、ダイアログ コントロールに表示します。 使用する必要があります、`DDX_*`メソッド (など`DDX_Text`) ではなく、`DDX_Field*`関数 (など`DDX_FieldText`) と`COleDbRecordView`します。 `DDX_FieldText` は動作しません`COleDbRecordView`ため`DDX_FieldText`型の追加の引数を取る`CRecordset*`(の`CRecordView`) または`CDaoRecordset*`(の`CDaoRecordView`)。

> [!NOTE]
>  OLE DB コンシューマー テンプレート クラスではなく、データ アクセス オブジェクト (DAO) クラスで作業している場合は、クラスを使用して[CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)代わりにします。 詳細については、この記事を参照してください。[概要。データベース プログラミング](../../data/data-access-programming-mfc-atl.md)します。

`COleDBRecordView` レコード ビューは、ユーザー インターフェイスを更新できるようにはの行セット内のユーザーの位置を追跡します。 ユーザーは、行セットの先頭または末尾に移動、レコード ビュー、ユーザー インターフェイス オブジェクトを無効にします: メニュー項目またはツール バー ボタンなど — を移動する同じ方向にさらにします。

行セット クラスの詳細については、次を参照してください。、[を使用して OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)記事。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxoledb.h

##  <a name="coledbrecordview"></a>  COleDBRecordView::COleDBRecordView

`COleDBRecordView` オブジェクトを構築します。

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>パラメーター

*lpszTemplateName*<br/>
ダイアログ テンプレート リソースの名前を表す null で終わる文字列が含まれています。

*nIDTemplate*<br/>
ダイアログ テンプレート リソースの ID 番号が含まれています。

### <a name="remarks"></a>Remarks

派生した型のオブジェクトを作成するときに`COleDBRecordView`、ビュー オブジェクトを作成し、ビューの基になるダイアログ リソースを識別するコンス トラクターの 1 つを呼び出します。 (コンス トラクターに渡す引数として文字列) の名前またはその ID (パスを符号なし整数の引数として) のいずれかのリソースを識別できます。

> [!NOTE]
>  派生クラスの*する必要があります*独自のコンス トラクターを指定します。 コンス トラクターで、コンス トラクターを呼び出す`COleDBRecordView::COleDBRecordView`リソース名または ID を引数として使用します。

##  <a name="ongetrowset"></a>  COleDBRecordView::OnGetRowset

ハンドルを返します、 **CRowset <>** レコード ビューに関連付けられているオブジェクト。

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

構築または行セット オブジェクトを取得して識別するハンドルを返す、には、このメンバー関数をオーバーライドする必要があります。 ClassWizard で、レコード ビュー クラスを宣言する場合、ウィザードの既定のオーバーライドを書き込みます。 ClassWizard の既定の実装では、1 つが存在する場合は、レコード ビューに格納されている行セット ハンドルを返します。 Classwizard で指定した場合は、型の行セット オブジェクトを作成しますが、その`Open`メンバー関数、テーブルを開くか、クエリを実行して、オブジェクトへのハンドルを返します。

> [!NOTE]
>  MFC 7.0 より前`OnGetRowset`へのポインターが返される`CRowset`します。 呼び出すコードがあれば`OnGetRowset`、テンプレート化されたクラスを戻り値の型を変更する必要がある**CRowset <>** します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

詳細と例については、この記事を参照してください。[レコード ビュー。レコード ビューを使用して](../../data/using-a-record-view-mfc-data-access.md)します。

##  <a name="onmove"></a>  COleDBRecordView::OnMove

表示行セット内の別のレコードに移動、レコードのコントロールでは、そのフィールドを表示します。

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>パラメーター

*nIDMoveCommand*<br/>
標準コマンド ID 値は次のいずれか:

- ID_RECORD_FIRST-は、レコード セットの最初のレコードに移動します。

- ID_RECORD_LAST-は、レコード セットのレコードで移動、最後にします。

- ID_RECORD_NEXT-は、レコード セットの次のレコードに移動します。

- ID_RECORD_PREV-は、レコード セットの前のレコードに移動します。

### <a name="return-value"></a>戻り値

移動が成功した場合、0 以外の場合移動要求が拒否された場合は 0 それ以外の場合。

### <a name="remarks"></a>Remarks

既定の実装は、適切な呼び出し`Move`のメンバー関数、`CRowset`レコード ビューに関連付けられているオブジェクト。

既定では、`OnMove`ユーザーを使用すると、レコード ビューに変更された場合は、データ ソースの現在のレコードを更新します。

アプリケーション ウィザードでは、最初のレコード、最後のレコード、次のレコード、および前のレコードのメニュー項目を含むメニュー リソースを作成します。 ツールバーのドッキング可能なオプションを選択すると、これらのコマンドに対応するボタンとツールバーは、アプリケーション ウィザードは、によっても作成します。

過去のレコード セットの最後のレコードを移動する場合、レコード ビューを最後のレコードの表示が続行されます。 過去の最初のレコード後方移動する場合、最初のレコードを表示するレコードの表示が続行されます。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)
