---
title: CRuntimeClass 構造体
ms.date: 11/04/2016
f1_keywords:
- CRuntimeClass
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
ms.openlocfilehash: 92979a10c18d9759e0ecc9f0785e56a97c0f0642
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372050"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass 構造体

各クラスから派生した`CObject`に関連付けられている、`CRuntimeClass`実行時にオブジェクトまたはその基底クラスに関する情報の取得に使用できる構造体。

## <a name="syntax"></a>構文

```
struct CRuntimeClass
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CRuntimeClass::CreateObject](#createobject)|実行時にオブジェクトを作成します。|
|[CRuntimeClass::FromName](#fromname)|使い慣れたクラス名を使用して、実行時に、オブジェクトを作成します。|
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|クラスは、指定したクラスから派生されているかどうかを決定します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|クラスの名前。|
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|オブジェクトのサイズ (バイト単位)。|
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|ポインター、`CRuntimeClass`基底クラスの構造体。|
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|動的にオブジェクトを作成する関数へのポインター。|
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|返します、 `CRuntimeClass` (時に動的に使用できるリンク) のみを構造体します。|
|[CRuntimeClass::m_wSchema](#m_wschema)|クラスのスキーマの数。|

## <a name="remarks"></a>Remarks

`CRuntimeClass` 構造体は、そのため、基底クラスはありません。

実行時にオブジェクトのクラスを特定する機能は、特別な型チェック関数の引数が必要な場合、またはオブジェクトのクラスに基づく特殊なコードを記述する必要がありますに便利です。 ランタイム クラス情報は、C++ 言語で直接サポートされていません。

`CRuntimeClass` ポインターなどの C++ オブジェクトの関連情報を提供します、`CRuntimeClass`の基本クラスと関連するクラスの ASCII クラス名。 この構造体は、既知の名前を使用して、関連するクラスは、特定のクラスから派生されているかどうかを決定するオブジェクトの種類を指定するオブジェクトを動的に作成するために使用できるさまざまな関数も実装します。

使用しての詳細については`CRuntimeClass`、記事をご覧ください[クラス情報にアクセスする](../../mfc/accessing-run-time-class-information.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

`CRuntimeClass`

## <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="createobject"></a>  CRuntimeClass::CreateObject

実行時に動的に指定したクラスを作成するには、この関数を呼び出します。

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>パラメーター

*lpszClassName*<br/>
作成するクラスの既知の名前。

### <a name="return-value"></a>戻り値

新しく作成したオブジェクトまたはクラス名が見つからないか、オブジェクトを作成する十分なメモリがある場合は NULL へのポインター。

### <a name="remarks"></a>Remarks

派生したクラス`CObject`動的作成は、実行時に指定したクラスのオブジェクトを作成する機能をサポートすることができます。 ドキュメント、ビュー、およびフレーム クラスでは、動的な作成をサポートする必要がありますなど。 動的な作成の詳細については、 `CreateObject` 、メンバーを参照してください[CObject クラス](../../mfc/using-cobject.md)と[CObject クラス。機能レベルを指定する](../../mfc/specifying-levels-of-functionality.md)します。

### <a name="example"></a>例

  例をご覧ください[IsDerivedFrom](#isderivedfrom)します。

##  <a name="fromname"></a>  CRuntimeClass::FromName

取得するには、この関数を呼び出し、`CRuntimeClass`使い慣れた名に関連付けられている構造体。

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>パラメーター

*lpszClassName*<br/>
派生したクラスの使い慣れた名前`CObject`します。

### <a name="return-value"></a>戻り値

ポインターを`CRuntimeClass`で渡されると、名前に対応するオブジェクト*lpszClassName*します。 一致するクラス名が見つからなかった場合は、NULL を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

##  <a name="isderivedfrom"></a>  CRuntimeClass::IsDerivedFrom

呼び出し元のクラスがで指定されたクラスから派生したかどうかを判断するには、この関数を呼び出し、*側*パラメーター。

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>パラメーター

*側*<br/>
派生したクラスの使い慣れた名前`CObject`します。

### <a name="return-value"></a>戻り値

TRUE の場合、クラスの呼び出し元`IsDerivedFrom`ベースからは派生クラス`CRuntimeClass`構造体は、パラメーターとして指定した場合は FALSE。

### <a name="remarks"></a>Remarks

リレーションシップについては、「ウォーキング」チェーン派生クラスのメンバーのクラスから最上位までによって決まります。 この関数は、基底クラスの一致が検出されない場合にのみ FALSE を返します。

> [!NOTE]
>  使用する、`CRuntimeClass`構造体、実行時のオブジェクトの情報を取得するクラスの実装では、新規クラス、IMPLEMENT_DYNCREATE、または IMPLEMENT_SERIAL マクロを含める必要があります。

使用しての詳細については`CRuntimeClass`、記事をご覧ください[CObject クラス。ランタイム クラス情報にアクセスする](../../mfc/accessing-run-time-class-information.md)します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

##  <a name="m_lpszclassname"></a>  CRuntimeClass::m_lpszClassName

ASCII のクラス名を含む null で終わる文字列。

### <a name="remarks"></a>Remarks

この名前を使用して、クラスのインスタンスを作成するために使用できます、`FromName`メンバー関数。

### <a name="example"></a>例

  例をご覧ください[IsDerivedFrom](#isderivedfrom)します。

##  <a name="m_nobjectsize"></a>  CRuntimeClass::m_nObjectSize

(バイト単位)、オブジェクトのサイズ。

### <a name="remarks"></a>Remarks

オブジェクトは、割り当てられたメモリを指すデータ メンバーを持っている場合はそのメモリのサイズは含まれません。

### <a name="example"></a>例

  例をご覧ください[IsDerivedFrom](#isderivedfrom)します。

##  <a name="m_pbaseclass"></a>  CRuntimeClass::m_pBaseClass

このデータ メンバーがへのポインターを格納する場合は、アプリケーションは、静的にリンクを`CRuntimeClass`基底クラスの構造体。

### <a name="remarks"></a>Remarks

アプリケーションは、MFC ライブラリに動的にリンクを場合、参照してください[m_pfnGetBaseClass](#m_pfngetbaseclass)します。

### <a name="example"></a>例

  例をご覧ください[IsDerivedFrom](#isderivedfrom)します。

##  <a name="m_pfncreateobject"></a>  CRuntimeClass::m_pfnCreateObject

クラスのオブジェクトを作成する既定のコンス トラクター関数のポインター。

### <a name="remarks"></a>Remarks

このポインターが有効なは、クラスは、動的作成をサポートしている場合のみそれ以外の場合、関数は、NULL を返します。

##  <a name="m_pfngetbaseclass"></a>  CRuntimeClass::m_pfnGetBaseClass

このデータ メンバーを返す関数を指すアプリケーションは、共有 DLL としての MFC ライブラリを使用する場合、`CRuntimeClass`基底クラスの構造体。

### <a name="remarks"></a>Remarks

アプリケーションに静的にリンクする場合、MFC ライブラリを参照してください。 [m_pBaseClass](#m_pbaseclass)します。

### <a name="example"></a>例

  例をご覧ください[IsDerivedFrom](#isderivedfrom)します。

##  <a name="m_wschema"></a>  CRuntimeClass::m_wSchema

スキーマの数 (シリアル化できないクラスの場合は-1)。

### <a name="remarks"></a>Remarks

スキーマ番号の詳細については、次を参照してください。、 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)マクロ。

### <a name="example"></a>例

  例をご覧ください[IsDerivedFrom](#isderivedfrom)します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
