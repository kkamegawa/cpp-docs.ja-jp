---
title: CAccessorBase クラス
ms.date: 11/04/2016
f1_keywords:
- CAccessorBase
- CAccessorBase.Close
- CAccessorBase::Close
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
- CAccessorBase::GetNumAccessors
- GetNumAccessors
- CAccessorBase.GetNumAccessors
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
helpviewer_keywords:
- CAccessorBase class
- Close method
- GetHAccessor method
- GetNumAccessors method
- IsAutoAccessor method
- ReleaseAccessors method
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
ms.openlocfilehash: 34c92f9057f2273d57b69bdb42c49a81923c3d2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284060"
---
# <a name="caccessorbase-class"></a>CAccessorBase クラス

OLE DB テンプレートのすべてのアクセサーは、このクラスから派生します。 `CAccessorBase` 複数のアクセサーを管理する 1 つの行セットを使用できます。 パラメーターと出力列の両方のバインドも提供します。

## <a name="syntax"></a>構文

```cpp
// Replace with syntax
```

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[閉じる](#close)|アクセサーを閉じます。|
|[GetHAccessor](#geth)|アクセサーのハンドルを取得します。|
|[GetNumAccessors](#getnum)|クラスによって作成されたアクセサーの数を取得します。|
|[IsAutoAccessor](#isauto)|指定されたアクセサーが自動かどうかをテストします。|
|[ReleaseAccessors](#release)|アクセサーを解放します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="close"></a> CAccessorBase::Close

アクセサーを閉じます。

### <a name="syntax"></a>構文

```cpp
void Close();
```

### <a name="remarks"></a>Remarks

呼び出す必要があります[ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md)最初。

## <a name="geth"></a> CAccessorBase::GetHAccessor

指定されたアクセサーのアクセサーのハンドルを取得します。

### <a name="syntax"></a>構文

```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>パラメーター

*nAccessor*<br/>
[in]アクセサーのゼロ オフセット番号。

### <a name="return-value"></a>戻り値

アクセサーのハンドルです。

## <a name="getnum"></a> CAccessorBase::GetNumAccessors

クラスによって作成されたアクセサーの数を取得します。

### <a name="syntax"></a>構文

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>戻り値

クラスによって作成されたアクセサーの数。

## <a name="isauto"></a> CAccessorBase::IsAutoAccessor

移動操作中に、アクセサーのデータが自動的に取得される場合に true を返します。

### <a name="syntax"></a>構文

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>パラメーター

*nAccessor*<br/>
[in]アクセサーのゼロ オフセット番号。

### <a name="return-value"></a>戻り値

返します**true**アクセサーが自動である場合。 それ以外の場合は **false**を返します。

## <a name="release"></a> CAccessorBase::ReleaseAccessors

クラスによって作成されたアクセサーを解放します。

### <a name="syntax"></a>構文

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>パラメーター

*pUnk*<br/>
[in]ポインター、`IUnknown`アクセサーが作成されている COM オブジェクトのインターフェイス。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

呼び出される[caccessorrowset::close](../../data/oledb/caccessorrowset-close.md)します。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessorBase クラス](../../data/oledb/caccessorbase-class.md)