---
title: マーシャ リングに関するグローバル関数
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: cac6e316ad6b5d3f49c171c940d9129060744aee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274695"
---
# <a name="marshaling-global-functions"></a>マーシャ リングに関するグローバル関数

これらの関数は、マーシャ リングとマーシャ リング データ インターフェイス ポインターに変換するサポートを提供します。

> [!IMPORTANT]
>  Windows ランタイムで実行するアプリケーションでは、次の表に示す関数を使用できません。

|||
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|マーシャ リング データを解放し、`IStream`ポインター。|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|新しいストリーム オブジェクトを作成し、指定されたインターフェイス ポインターをマーシャ リングします。|
|[AtlUnmarshalPtr](#atlunmarshalptr)|インターフェイス ポインターには、ストリームのマーシャ リング データを変換します。|

## <a name="requirements"></a>要件:

**ヘッダー:** atlbase.h

##  <a name="atlfreemarshalstream"></a>  AtlFreeMarshalStream

ストリーム内のマーシャリング データを解放し、次にストリーム ポインターも解放します。

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>パラメーター

*pStream*<br/>
[in]ポインター、`IStream`インターフェイスのマーシャ リングするために使用するストリーム。

### <a name="example"></a>例

例をご覧ください[AtlMarshalPtrInProc](#atlmarshalptrinproc)します。

##  <a name="atlmarshalptrinproc"></a>  AtlMarshalPtrInProc

新しいストリーム オブジェクトを作成し、プロキシの CLSID をストリームに書き込みます。さらに、プロキシの初期化に必要なデータをストリームに書き込んで、指定されたインターフェイス ポインターをマーシャリングします。

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>パラメーター

*pUnk*<br/>
[in]マーシャ リングするインターフェイスへのポインター。

*iid*<br/>
[in]マーシャ リングされるインターフェイスの GUID です。

*ppStream*<br/>
[out]ポインター、`IStream`マーシャ リングするため、新しいストリーム オブジェクトのインターフェイス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

MSHLFLAGS_TABLESTRONG フラグは設定されているため、複数のストリームにポインターをマーシャ リングすることができます。 ポインターもいないマーシャ リングされた複数回できます。

失敗をマーシャ リングする場合は、ストリーム ポインターが解放されます。

`AtlMarshalPtrInProc` プロセスでオブジェクトへのポインターでのみ使用できます。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

##  <a name="atlunmarshalptr"></a>  AtlUnmarshalPtr

ストリームのマーシャリング データをクライアントが使用できるインターフェイス ポインターに変換します。

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>パラメーター

*pStream*<br/>
[in]マーシャ リング解除されているストリームへのポインター。

*iid*<br/>
[in]マーシャ リング解除されているインターフェイスの GUID です。

*ppUnk*<br/>
[out]マーシャ リング解除されたインターフェイスへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="example"></a>例

例をご覧ください[AtlMarshalPtrInProc](#atlmarshalptrinproc)します。

## <a name="see-also"></a>関連項目

[関数](../../atl/reference/atl-functions.md)
