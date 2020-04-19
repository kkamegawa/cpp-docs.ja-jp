---
title: ICommandTextImpl クラス
ms.date: 11/04/2016
f1_keywords:
- ICommandText
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
- ATL::ICommandTextImpl::m_strCommandText
- ICommandTextImpl<T>::m_strCommandText
- m_strCommandText
- ICommandTextImpl.m_strCommandText
- ICommandTextImpl::m_strCommandText
- ATL::ICommandTextImpl<T>::m_strCommandText
- ATL.ICommandTextImpl.m_strCommandText
- ICommandTextImpl.SetCommandText
- ICommandTextImpl::SetCommandText
- SetCommandText
helpviewer_keywords:
- ICommandText class
- GetCommandText method
- m_strCommandText
- SetCommandText method
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
ms.openlocfilehash: de9e930056db7b91968ca1ce471a87809693376a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408980"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl クラス

実装を提供、 [ICommandText](/previous-versions/windows/desktop/ms714914(v=vs.85))インターフェイス。

## <a name="syntax"></a>構文

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>パラメーター

*T*<br/>
コマンド クラスから派生した`ICommandTextImpl`します。

## <a name="requirements"></a>必要条件

**ヘッダー:** altdb.h

## <a name="members"></a>メンバー

### <a name="interface-methods"></a>インターフェイス メソッド

|||
|-|-|
|[GetCommandText](#getcommandtext)|テキスト コマンドの最後の呼び出しでセットを返します[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)します。|
|[SetCommandText](#setcommandtext)|既存のコマンド テキストを置き換えて、コマンド テキストを設定します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[m_strCommandText](#strcommandtext)|コマンド テキストを格納します。|

## <a name="remarks"></a>Remarks

コマンドの必須インターフェイス。

## <a name="getcommandtext"></a> ICommandTextImpl::GetCommandText

テキスト コマンドの最後の呼び出しでセットを返します[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>パラメーター

参照してください[ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。 *既定で*パラメーターは既定では無視されます。

## <a name="setcommandtext"></a> ICommandTextImpl::SetCommandText

既存のコマンド テキストを置き換えて、コマンド テキストを設定します。

### <a name="syntax"></a>構文

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>パラメーター

参照してください[icommandtext::setcommandtext](/previous-versions/windows/desktop/ms709757(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

## <a name="strcommandtext"></a> ICommandTextImpl::m_strCommandText

コマンド テキストの文字列を格納します。

### <a name="syntax"></a>構文

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレート](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)