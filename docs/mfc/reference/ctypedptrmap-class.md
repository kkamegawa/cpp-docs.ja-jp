---
title: CTypedPtrMap クラス
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
ms.openlocfilehash: bc164125f867cf3e2f27b74e69b826cbed31ff1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323571"
---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap クラス

ポインター マップ クラス `CMapPtrToPtr`、 `CMapPtrToWord`、 `CMapWordToPtr`、および `CMapStringToPtr`のオブジェクトに対してタイプ セーフな "ラップ" が用意されています。

## <a name="syntax"></a>構文

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>パラメーター

*BASE_CLASS*<br/>
型指定されたポインター マップ クラスの基本クラスポインター マップ クラスでなければなりません ( `CMapPtrToPtr`、 `CMapPtrToWord`、 `CMapWordToPtr`、または`CMapStringToPtr`)。

*KEY*<br/>
マップのキーとして使用されるオブジェクトのクラスです。

*値*<br/>
マップに格納されるオブジェクトのクラスです。

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|反復処理するためには、次の要素を取得します。|
|[CTypedPtrMap::Lookup](#lookup)|返します、`KEY`に基づいて、`VALUE`します。|
|[CTypedPtrMap::RemoveKey](#removekey)|キーで指定された要素を削除します。|
|[CTypedPtrMap::SetAt](#setat)|マップに要素を挿入します。一致するキーが見つかった場合は、既存の要素を置き換えます。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CTypedPtrMap::operator \[ \]](#operator_at)|Map に要素を挿入します。|

## <a name="remarks"></a>Remarks

使用すると`CTypedPtrMap`C++ の型チェック機能は、一致しないポインター型で発生したエラーを解消します。

すべて`CTypedPtrMap`関数はインラインで、このテンプレートの使用が大幅には影響しません、コードの速度またはサイズ。

使用しての詳細については`CTypedPtrMap`、記事を参照して[コレクション](../../mfc/collections.md)と[クラスのテンプレートに基づく](../../mfc/template-based-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtempl.h

##  <a name="getnextassoc"></a>  CTypedPtrMap::GetNextAssoc

マップ要素を取得`rNextPosition`、し更新`rNextPosition`にマップの次の要素を参照してください。

```
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>パラメーター

*rPosition*<br/>
によって以前返される位置の値への参照を指定します`GetNextAssoc`または`BASE_CLASS` **:: 中**呼び出します。

*KEY*<br/>
マップのキーの種類を指定するテンプレート パラメーター。

*rKey*<br/>
取得した要素の返されたキーを指定します。

*値*<br/>
マップの値の型を指定するテンプレート パラメーター。

*rValue*<br/>
取得した要素の戻り値を指定します。

### <a name="remarks"></a>Remarks

この関数のマップのすべての要素を反復処理する最も便利です。 位置の順序は必ずしもキー値のシーケンスと同じに注意してください。

場合は、取得した最後の要素をマップでは、次の新しい値`rNextPosition`NULL に設定されます。

このインライン関数`BASE_CLASS` **:: たどる**します。

##  <a name="lookup"></a>  CTypedPtrMap::Lookup

`Lookup` ハッシュ アルゴリズムを使用して、すばやく正確に一致するキーを使用して、マップの要素を検索します。

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>パラメーター

*BASE_CLASS*<br/>
このマップのクラスの基本クラスを指定するテンプレート パラメーター。

*key*<br/>
検索する要素のキー。

*値*<br/>
このマップに格納されている値の型を指定するテンプレート パラメーター。

*rValue*<br/>
取得した要素の戻り値を指定します。

### <a name="return-value"></a>戻り値

要素が見つかった場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

このインライン関数`BASE_CLASS` **:: 参照**します。

##  <a name="operator_at"></a>  CTypedPtrMap::operator [ ]

この演算子は、代入ステートメント (左辺値) の左側でのみ使用できます。

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>パラメーター

*値*<br/>
このマップに格納されている値の型を指定するテンプレート パラメーター。

*BASE_CLASS*<br/>
このマップのクラスの基本クラスを指定するテンプレート パラメーター。

*key*<br/>
データベースを検索するか、またはマップで作成する要素のキー。

### <a name="remarks"></a>Remarks

指定したキーにマップ要素が存在しない、新しい要素が作成されます。 ありません「右側」(右辺値) この演算子と同じキーは、マップには存在しない可能性があるためです。 使用して、`Lookup`メンバー関数は要素を取得します。

##  <a name="removekey"></a>  CTypedPtrMap::RemoveKey

このメンバー関数を呼び出す`BASE_CLASS` **:: は**します。

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>パラメーター

*KEY*<br/>
マップのキーの種類を指定するテンプレート パラメーター。

*key*<br/>
削除する要素をキーします。

### <a name="return-value"></a>戻り値

エントリが見つかり、正常に削除された場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

詳細についてを参照してください。 [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)します。

##  <a name="setat"></a>  CTypedPtrMap::SetAt

このメンバー関数を呼び出す`BASE_CLASS` **:: SetAt**します。

```
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>パラメーター

*KEY*<br/>
マップのキーの種類を指定するテンプレート パラメーター。

*key*<br/>
NewValue のキーの値を指定します。

*newValue*<br/>
新しい要素の値であるオブジェクトのポインターを指定します。

### <a name="remarks"></a>Remarks

詳細についてを参照してください。 [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)します。

## <a name="see-also"></a>関連項目

[MFC サンプルの収集](../../overview/visual-cpp-samples.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr クラス](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord クラス](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapWordToPtr クラス](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[CMapStringToPtr クラス](../../mfc/reference/cmapstringtoptr-class.md)
