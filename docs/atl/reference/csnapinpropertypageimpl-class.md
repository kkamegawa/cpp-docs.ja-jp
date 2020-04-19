---
title: CSnapInPropertyPageImpl クラス
ms.date: 11/04/2016
f1_keywords:
- CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CancelToClose
- ATLSNAP/ATL::CSnapInPropertyPageImpl::Create
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnApply
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnHelp
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnKillActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnQueryCancel
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnReset
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnSetActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardBack
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardFinish
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardNext
- ATLSNAP/ATL::CSnapInPropertyPageImpl::QuerySiblings
- ATLSNAP/ATL::CSnapInPropertyPageImpl::SetModified
- ATLSNAP/ATL::CSnapInPropertyPageImpl::m_psp
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
ms.openlocfilehash: abf4cf5804f6ef7335192feb298f1a4a06f841e4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496392"
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl クラス

このクラスには、スナップインプロパティページオブジェクトを実装するためのメソッドが用意されています。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|**[OK]** ボタンと **[キャンセル**] ボタンの状態を変更します。|
|[CSnapInPropertyPageImpl::Create](#create)|新しく作成され`CSnapInPropertyPageImpl`たオブジェクトを初期化します。|
|[CSnapInPropertyPageImpl:: OnApply](#onapply)|ウィザード型のプロパティシートを使用しているときに、ユーザーが **[今すぐ適用]** ボタンをクリックしたときにフレームワークによって呼び出されます。|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|ウィザード型のプロパティシートを使用しているときにユーザーが **[ヘルプ]** ボタンをクリックしたときに、フレームワークによって呼び出されます。|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|現在のページがアクティブでなくなったときにフレームワークによって呼び出されます。|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|キャンセルが行われる前に、ユーザーが **[キャンセル**] ボタンをクリックしたときにフレームワークによって呼び出されます。|
|[CSnapInPropertyPageImpl:: OnReset](#onreset)|ウィザード型のプロパティシートを使用しているときに、ユーザーが **[リセット]** ボタンをクリックしたときにフレームワークによって呼び出されます。|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|現在のページがアクティブになったときにフレームワークによって呼び出されます。|
|[CSnapInPropertyPageImpl:: OnWizardBack](#onwizardback)|ウィザード型のプロパティシートを使用しているときに、ユーザーが **[戻る]** ボタンをクリックしたときにフレームワークによって呼び出されます。|
|[CSnapInPropertyPageImpl:: OnWizardFinish](#onwizardfinish)|ウィザード型のプロパティシートを使用しているときに、ユーザーが **[完了**] ボタンをクリックしたときにフレームワークによって呼び出されます。|
|[CSnapInPropertyPageImpl:: OnWizardNext](#onwizardnext)|ウィザード型のプロパティシートを使用しているときに、ユーザーが **[次へ**] ボタンをクリックしたときにフレームワークによって呼び出されます。|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|現在のメッセージをプロパティシートのすべてのページに転送します。|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|を呼び出して、 **[今すぐ適用]** ボタンをアクティブまたは非アクティブにします。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|オブジェクトによって使用される Windows `PROPSHEETPAGE`構造体。 `CSnapInPropertyPageImpl`|

## <a name="remarks"></a>Remarks

`CSnapInPropertyPageImpl`スナップインプロパティページオブジェクトの基本的な実装を提供します。 スナップインのプロパティページの基本的な機能は、いくつかの異なるインターフェイスとマップの種類を使用して実装されます。

## <a name="inheritance-hierarchy"></a>継承階層

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsnap. h

##  <a name="canceltoclose"></a>CSnapInPropertyPageImpl::CancelToClose

モーダルプロパティシートのページ内のデータに回復不可能な変更が加えられた後に、この関数を呼び出します。

```
void CancelToClose();
```

### <a name="remarks"></a>Remarks

この関数は、 **[OK** ] ボタンを**閉じ**て **[キャンセル**] ボタンを無効にします。 この変更により、変更が永続的であり、変更を取り消すことができないことがユーザーに通知されます。

この`CancelToClose`メンバー関数は、モードレスプロパティシートでは何も実行しません。既定では、モードレスプロパティシートに **[キャンセル**] ボタンがないためです。

##  <a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

`CSnapInPropertyPageImpl` オブジェクトを構築します。

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszTitle*<br/>
からプロパティページのタイトル。

### <a name="remarks"></a>Remarks

基になる構造体を初期化するには、 [CSnapInPropertyPageImpl:: Create](#create)を呼び出します。

##  <a name="create"></a>  CSnapInPropertyPageImpl::Create

この関数を呼び出して、プロパティページの基になる構造を初期化します。

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>戻り値

新しく作成され`PROPSHEETPAGE`たプロパティシートの属性を格納している構造体へのハンドル。

### <a name="remarks"></a>Remarks

この関数を呼び出す前に、まず[CSnapInPropertyPageImpl:: CSnapInPropertyPageImpl](#csnapinpropertypageimpl)を呼び出してください。

##  <a name="m_psp"></a>  CSnapInPropertyPageImpl::m_psp

`m_psp`は、の`PROPSHEETPAGE`特性を格納するメンバーを持つ構造体です。

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Remarks

この構造体を使用して、プロパティページの構築後に外観を初期化します。

メンバーの一覧など、この構造の詳細については、Windows SDK の「 [Propsheet ページ](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3)」を参照してください。

##  <a name="onapply"></a>CSnapInPropertyPageImpl:: OnApply

このメンバー関数は、ユーザーが **[OK]** または **[今すぐ適用]** ボタンをクリックしたときに呼び出されます。

```
BOOL OnApply();
```

### <a name="return-value"></a>戻り値

変更が受け入れられた場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

が`OnApply`フレームワークによって呼び出されるようにするには`SetModified` 、を呼び出し、そのパラメーターを TRUE に設定する必要があります。 これにより、ユーザーがプロパティページを変更するとすぐに **[今すぐ適用]** ボタンがアクティブになります。

このメンバー関数をオーバーライドして、ユーザーが **[今すぐ適用]** ボタンをクリックしたときにプログラムが実行するアクションを指定します。 オーバーライドする場合、関数は変更を受け入れるには TRUE を返し、変更が有効にならないように FALSE を返します。

の既定の`OnApply`実装では、TRUE が返されます。

##  <a name="onhelp"></a>CSnapInPropertyPageImpl::OnHelp

このメンバー関数は、ユーザーがプロパティページの **[ヘルプ]** ボタンをクリックしたときに呼び出されます。

```
void OnHelp();
```

### <a name="remarks"></a>Remarks

プロパティページのヘルプを表示するには、このメンバー関数をオーバーライドします。

##  <a name="onkillactive"></a>  CSnapInPropertyPageImpl::OnKillActive

このメンバー関数は、ページがアクティブページでなくなったときに呼び出されます。

```
BOOL OnKillActive();
```

### <a name="return-value"></a>戻り値

データが正常に更新された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

特別なデータ検証タスクを実行するには、このメンバー関数をオーバーライドします。

##  <a name="onquerycancel"></a>  CSnapInPropertyPageImpl::OnQueryCancel

このメンバー関数は、ユーザーが **[キャンセル]** をクリックしたときと、キャンセル操作が行われる前に呼び出されます。

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>戻り値

取り消し操作を許可する場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメンバー関数をオーバーライドして、ユーザーが **[キャンセル**] ボタンをクリックしたときにプログラムが実行するアクションを指定します。

の既定の`OnQueryCancel`実装では、TRUE が返されます。

##  <a name="onreset"></a>CSnapInPropertyPageImpl:: OnReset

このメンバー関数は、ユーザーが **[キャンセル**] ボタンをクリックしたときに呼び出されます。

```
void OnReset();
```

### <a name="remarks"></a>Remarks

この関数を呼び出すと、ユーザーが **[今すぐ適用]** ボタンをクリックしたときに行われたすべてのプロパティページへの変更が破棄され、プロパティシートがフォーカスを保持します。

このメンバー関数をオーバーライドして、ユーザーが **[キャンセル**] ボタンをクリックしたときにプログラムが実行するアクションを指定します。

##  <a name="onsetactive"></a>  CSnapInPropertyPageImpl::OnSetActive

このメンバー関数は、ページがユーザーによって選択され、アクティブページになると呼び出されます。

```
BOOL OnSetActive();
```

### <a name="return-value"></a>戻り値

ページが正常にアクティブに設定された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

ページがアクティブになったときにタスクを実行するには、このメンバー関数をオーバーライドします。 このメンバー関数のオーバーライドでは、他の処理が行われる前に、既定のバージョンを呼び出す必要があります。

既定の実装では、TRUE が返されます。

##  <a name="onwizardback"></a>CSnapInPropertyPageImpl:: OnWizardBack

このメンバー関数は、ユーザーがウィザードの **[戻る]** ボタンをクリックしたときに呼び出されます。

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>戻り値

- 0を設定すると、前のページに自動的に進みます。

- ページが変更されないようにする場合は-1。

次のページ以外のページにジャンプするには、表示されるダイアログボックスの識別子を返します。

### <a name="remarks"></a>Remarks

このメンバー関数をオーバーライドして、 **[戻る]** ボタンがクリックされたときにユーザーが実行する必要のあるアクションを指定します。

##  <a name="onwizardfinish"></a>CSnapInPropertyPageImpl:: OnWizardFinish

このメンバー関数は、ユーザーがウィザードの **[完了**] ボタンをクリックしたときに呼び出されます。

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>戻り値

ウィザードの終了時にプロパティシートが破棄される場合は0以外。それ以外の場合は0。

### <a name="remarks"></a>Remarks

このメンバー関数をオーバーライドして、 **[完了**] ボタンをクリックしたときにユーザーが実行する必要のあるアクションを指定します。

##  <a name="onwizardnext"></a>CSnapInPropertyPageImpl:: OnWizardNext

このメンバー関数は、ユーザーがウィザードの **[次へ]** ボタンをクリックしたときに呼び出されます。

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>戻り値

- 0を設定すると、次のページに自動的に進みます。

- ページが変更されないようにする場合は-1。

次のページ以外のページにジャンプするには、表示されるダイアログボックスの識別子を返します。

### <a name="remarks"></a>Remarks

このメンバー関数をオーバーライドして、 **[次へ**] ボタンをクリックしたときにユーザーが実行する必要のあるアクションを指定します。

##  <a name="querysiblings"></a>  CSnapInPropertyPageImpl::QuerySiblings

このメンバー関数を呼び出して、プロパティシート内の各ページにメッセージを転送します。

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>パラメーター

*wParam*<br/>
から追加のメッセージに依存する情報を指定します。

*lParam*<br/>
から追加のメッセージに依存する情報を指定します。

### <a name="return-value"></a>戻り値

メッセージを次のプロパティページに転送しない場合は0以外の値。それ以外の場合は0。

### <a name="remarks"></a>Remarks

ページから0以外の値が返された場合、プロパティシートは後続のページにメッセージを送信しません。

##  <a name="setmodified"></a>CSnapInPropertyPageImpl::SetModified

このメンバー関数を呼び出して、プロパティページの設定を適切な外部オブジェクトに適用するかどうかに基づいて **[今すぐ適用]** ボタンを有効または無効にします。

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>パラメーター

*bChanged*<br/>
からプロパティページの設定が最後に適用されてから変更されたことを示す場合は TRUE。プロパティページの設定が適用されていることを示す場合は FALSE、無視する場合はです。

### <a name="remarks"></a>Remarks

プロパティシートは、どのページが "ダーティ" であるかを追跡します。これは、を呼び出し`SetModified( TRUE )`たときのプロパティページです。 いずれかのページに対してを呼び出し`SetModified( TRUE )`た場合、 **[今すぐ適用]** ボタンは常に有効になります。 **[今すぐ適用]** ボタンは、いずれかの`SetModified( FALSE )`ページに対してを呼び出すと無効になりますが、他のどのページも "ダーティ" になっている場合のみです。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
