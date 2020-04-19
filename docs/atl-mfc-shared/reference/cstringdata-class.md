---
title: CStringData クラス
ms.date: 11/04/2016
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
ms.openlocfilehash: 5977d26cade89f2e70453d5184323958e99e54c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198138"
---
# <a name="cstringdata-class"></a>CStringData クラス

このクラスは、文字列オブジェクトのデータを表します。

## <a name="syntax"></a>構文

```
struct CStringData
```

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[AddRef](#addref)|文字列のデータ オブジェクトの参照カウントをインクリメントします。|
|[data](#data)|文字列オブジェクトの文字データを取得します。|
|[IsLocked](#islocked)|関連付けられている文字列オブジェクトのバッファーがロックされているかどうかを決定します。|
|[とき](#isshared)|関連付けられている文字列オブジェクトのバッファーの現在の共有かどうかを決定します。|
|[ロック](#lock)|関連付けられている文字列オブジェクトのバッファーをロックします。|
|[Release](#release)|指定された文字列オブジェクトを解放します。|
|[ロックを解除します。](#unlock)|関連付けられている文字列オブジェクトのバッファーのロックを解除します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[nAllocLength](#nalloclength)|割り当てられているデータの長さ`XCHAR`s (終端の null) などではありません|
|[nDataLength](#ndatalength)|現在使用されているデータの長さ`XCHAR`s (終端の null) などではありません|
|[nRefs](#nrefs)|オブジェクトの現在の参照カウントします。|
|[pStringMgr](#pstringmgr)|この文字列オブジェクトの文字列のマネージャーへのポインター。|

## <a name="remarks"></a>Remarks

このクラスは、開発者がカスタム文字列マネージャーの実装のみが使用する必要があります。 カスタム文字列マネージャーの詳細については、次を参照してください[メモリ管理と CStringT。](../../atl-mfc-shared/memory-management-with-cstringt.md)

このクラスは、さまざまな種類の情報となどの上位の文字列オブジェクトに関連付けられているデータをカプセル化[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)、 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)、または[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)オブジェクト。 ごとの上位の文字列オブジェクトには、それに関連付けられたへのポインターが含まれています。`CStringData`オブジェクト、複数の文字列オブジェクトと同じ文字列のデータ オブジェクトを指すことができます。 この関係は、参照カウントによって表される (`nRefs`) の`CStringData`オブジェクト。

> [!NOTE]
>  特定の場合、文字列型 (など`CFixedString`) は、上位の 1 つ以上の文字列オブジェクトを文字列のデータ オブジェクトを共有していません。 詳細については、これは、次を参照してください。[メモリ管理と CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)します。

このデータで構成されます。

- メモリ マネージャー (型の[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) の文字列。

- 現在の長さ ( [nDataLength](#ndatalength)) の文字列。

- 割り当て済みの長さ ( [nAllocLength](#nalloclength)) の文字列。 パフォーマンス上の理由から、これは異なる場合、現在の文字列の長さ

- 現在の参照カウント ( [nRefs](#nrefs)) の`CStringData`オブジェクト。 この値が同じ共有文字列オブジェクトの数を決定するで使用される`CStringData`オブジェクト。

- 実際の文字バッファー ([データ](#data)) の文字列。

   > [!NOTE]
   > 文字列オブジェクトの実際の文字バッファー文字列マネージャーが割り当てられるし、に追加される、`CStringData`オブジェクト。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsimpstr.h

##  <a name="addref"></a>  CStringData::AddRef

文字列オブジェクトの参照カウントをインクリメントします。

```
void AddRef() throw();
```

### <a name="remarks"></a>Remarks

文字列オブジェクトの参照カウントをインクリメントします。

> [!NOTE]
>  負の数は、文字列バッファーがロックされていることを示すために、負の値の参照カウントを持つ文字列をこのメソッドを呼び出さないでください。

##  <a name="data"></a>  CStringData::data

文字列オブジェクトの文字バッファーへのポインターを返します。

```
void* data() throw();
```

### <a name="return-value"></a>戻り値

文字列オブジェクトの文字バッファーへのポインター。

### <a name="remarks"></a>Remarks

この関数では、関連付けられている文字列オブジェクトの現在の文字バッファーを返します。

> [!NOTE]
>  このバッファーがによって割り当てられていない、`CStringData`オブジェクトが必要なときに、文字列マネージャーでします。 割り当てられると、バッファーが文字列データ オブジェクトに追加されます。

##  <a name="islocked"></a>  CStringData::IsLocked

文字バッファーがロックされているかどうかを決定します。

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>戻り値

バッファーはロックされているかどうかは TRUE を返しますそれ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

文字列オブジェクトの文字バッファーがロックされているかどうかを判断するには、この関数を呼び出します。

##  <a name="isshared"></a>  CStringData::IsShared

文字バッファーを共有するかどうかを決定します。

```
bool IsShared() const throw();
```

### <a name="return-value"></a>戻り値

かどうか、バッファーが共有されます。 TRUE を返しますそれ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

文字列のデータ オブジェクトの文字バッファーの複数の文字列オブジェクトで現在の共有かどうかを判断するには、この関数を呼び出します。

##  <a name="lock"></a>  CStringData::Lock

関連付けられている文字列オブジェクトの文字バッファーをロックします。

```
void Lock() throw();
```

### <a name="remarks"></a>Remarks

文字列のデータ オブジェクトの文字バッファーをロックするには、この関数を呼び出します。 ロックおよびロック解除は、開発者が文字バッファーへの直接アクセスが必要な場合に使用されます。 ロックの好例が示されている、 [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)と[として](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)メソッドの`CSimpleStringT`します。

> [!NOTE]
>  バッファーが上位の文字列オブジェクト間で共有されていない場合、文字バッファーをロックだけことができます。

##  <a name="nalloclength"></a>  CStringData::nAllocLength

割り当てられた文字バッファーの長さ。

```
int nAllocLength;
```

### <a name="remarks"></a>Remarks

割り当て済みのデータ バッファーの長さを格納`XCHAR`s (終端の null) などではありません。

##  <a name="ndatalength"></a>  CStringData::nDataLength

文字列オブジェクトの現在の長さ。

```
int nDataLength;
```

### <a name="remarks"></a>Remarks

現在使用されているデータの長さを格納`XCHAR`s (終端の null) などではありません。

##  <a name="nrefs"></a>  CStringData::nRefs

文字列のデータ オブジェクトの参照カウント。

```
long nRefs;
```

### <a name="remarks"></a>Remarks

文字列のデータ オブジェクトの参照カウントを格納します。 この数は、文字列データ オブジェクトに関連付けられている上位の文字列オブジェクトの数を示します。 負の値は、文字列データ オブジェクトが現在ロックされていることを示します。

##  <a name="pstringmgr"></a>  CStringData::pStringMgr

関連付けられている文字列オブジェクトのメモリ マネージャー。

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>Remarks

関連付けられている文字列オブジェクトのメモリ マネージャーが格納されます。 メモリ マネージャーと文字列の詳細については、次を参照してください。[メモリ管理と CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)します。

##  <a name="release"></a>  CStringData::Release

文字列のデータ オブジェクトの参照カウントをデクリメントします。

```
void Release() throw();
```

### <a name="remarks"></a>Remarks

参照カウントをデクリメントするには、この関数を呼び出す解放、`CStringData`参照カウントがゼロの場合に構造体します。 文字列オブジェクトが削除され、そのため、文字列のデータ オブジェクトを参照する必要もなくなりましたときにこれは一般的です。

たとえば、次のコードは呼び出します`CStringData::Release`文字列データ オブジェクトに関連付けられたの`str1`:

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

##  <a name="unlock"></a>  CStringData::Unlock

関連付けられている文字列オブジェクトの文字バッファーのロックを解除します。

```
void Unlock() throw();
```

### <a name="remarks"></a>Remarks

文字列のデータ オブジェクトの文字バッファーのロックを解除するには、この関数を呼び出します。 バッファーのロックが解除とは共有可能な参照をカウントできます。

> [!NOTE]
>  呼び出しごとに`Lock`に対応する呼び出しから一致する必要があります`Unlock`します。

ロックおよびロック解除は、開発者は、文字列データを共有しないことを確認する必要があるときに使用されます。 ロックの好例が示されている、 [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)と[として](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)メソッドの`CSimpleStringT`します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)
