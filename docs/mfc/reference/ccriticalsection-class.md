---
title: CCriticalSection クラス
ms.date: 11/04/2016
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
ms.openlocfilehash: 2c89647afc8a9a8c6564d25afe20d48818a643f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385379"
---
# <a name="ccriticalsection-class"></a>CCriticalSection クラス

「クリティカル セクション」を表します: リソースまたはコード セクションへのアクセスには、一度に 1 つのスレッドをできるようにする同期オブジェクト。

## <a name="syntax"></a>構文

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CCriticalSection::CCriticalSection](#ccriticalsection)|`CCriticalSection` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CCriticalSection::Lock](#lock)|アクセスするために使用して、`CCriticalSection`オブジェクト。|
|[CCriticalSection::Unlock](#unlock)|`CCriticalSection` のオブジェクトを解放します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CCriticalSection::operator CRITICAL_SECTION*](#operator_critical_section_star)|内部の CRITICAL_SECTION オブジェクトへのポインターを取得します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CCriticalSection::m_sect](#m_sect)|CRITICAL_SECTION オブジェクト。|

## <a name="remarks"></a>Remarks

重要なセクションは、データまたはその他の制御されたリソースの変更を一度に 1 つのスレッドができる場合に便利です。 たとえば、リンク リスト ノードの追加は、一度に 1 つのスレッドでのみ許可するプロセスです。 使用して、`CCriticalSection`だけで、一覧に、一度に 1 つのスレッドがアクセスできるリンクのリストを制御するオブジェクト。

> [!NOTE]
>  機能、`CCriticalSection`クラスは、実際の Win32 CRITICAL_SECTION オブジェクトによって提供されます。

重要なセクションは、ミュー テックスの代わりに使用されます (を参照してください[CMutex](../../mfc/reference/cmutex-class.md)) と速度が重要なプロセス境界をまたいでリソースは使用されません。

2 つのメソッドを使用するため、`CCriticalSection`オブジェクト: スタンドアロンおよび埋め込みクラスにします。

- スタンドアロンを使用するスタンドアロン メソッド`CCriticalSection`オブジェクト、構築、`CCriticalSection`必要がある場合のオブジェクトします。 呼び出してオブジェクトを明示的にコンス トラクターから正常に返された後にロック[ロック](#lock)します。 呼び出す[Unlock](#unlock)が終わったら、クリティカル セクションにアクセスします。 だれかが、ソース コードを読むにはわかり、このメソッドは、ロックし、アクセスの前後にクリティカル セクションのロックを解除することが、エラーが発生しやすいです。

   望ましいメソッドは、使用する、 [CSingleLock](../../mfc/reference/csinglelock-class.md)クラス。 また、`Lock`と`Unlock`メソッドは、例外が発生した場合、リソースのロックを解除について心配する必要はありません。

- メソッドを追加することで、複数のスレッドでクラスを共有することもできますを埋め込み、 `CCriticalSection`-クラスと必要なときに、データ メンバーをロックする型のデータ メンバー。

使用しての詳細については`CCriticalSection`オブジェクトは、記事をご覧ください。[マルチ スレッド。同期クラスの使用方法](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxmt.h

##  <a name="ccriticalsection"></a>  CCriticalSection::CCriticalSection

`CCriticalSection` オブジェクトを構築します。

```
CCriticalSection();
```

### <a name="remarks"></a>Remarks

アクセスまたはリリースを`CCriticalSection`オブジェクトを作成、 [CSingleLock](../../mfc/reference/csinglelock-class.md)オブジェクトと呼び出しの[ロック](../../mfc/reference/csinglelock-class.md#lock)と[Unlock](../../mfc/reference/csinglelock-class.md#unlock)メンバー関数。 場合、`CCriticalSection`オブジェクトがスタンドアロンの使用にされている場合、呼び出しの[ロックの解除](#unlock)メンバー関数は、それを解放します。

コンス トラクターが必要なシステム メモリ、メモリ不足の例外の割り当てに失敗するかどうか (型の[CMemoryException](../../mfc/reference/cmemoryexception-class.md)) が自動的にスローされます。

### <a name="example"></a>例

  例をご覧ください[CCriticalSection::Lock](#lock)します。

##  <a name="lock"></a>  CCriticalSection::Lock

クリティカル セクション オブジェクトにアクセスするには、このメンバー関数を呼び出します。

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>パラメーター

*dwTimeout*<br/>
`Lock` このパラメーターの値は無視されます。

### <a name="return-value"></a>戻り値

関数が成功した場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

`Lock` クリティカル セクション オブジェクトがシグナル状態になるまでは返されませんをブロッキング呼び出し (利用になります)。

使用することができますがタイムアウトしました待機が必要な場合、 [CMutex](../../mfc/reference/cmutex-class.md)オブジェクトの代わりに、`CCriticalSection`オブジェクト。

場合`Lock`がメモリ不足の例外であり、必要なシステム メモリの割り当てに失敗した (型の[CMemoryException](../../mfc/reference/cmemoryexception-class.md)) が自動的にスローされます。

### <a name="example"></a>例

この例では、共有リソースへのアクセスを制御することで、入れ子になったのクリティカル セクションの方法を示します (静的な`_strShared`オブジェクト)、共有を使用して`CCriticalSection`オブジェクト。 `SomeMethod`関数では、安全な方法での共有リソースの更新について説明します。

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

##  <a name="m_sect"></a>  CCriticalSection::m_sect

すべてで使用されるクリティカル セクション オブジェクトを含む`CCriticalSection`メソッド。

```
CRITICAL_SECTION m_sect;
```

##  <a name="operator_critical_section_star"></a>  CCriticalSection::operator CRITICAL_SECTION*

したがって、CRITICAL_SECTION オブジェクトを取得します。

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>Remarks

内部の CRITICAL_SECTION オブジェクトへのポインターを取得するには、この関数を呼び出します。

##  <a name="unlock"></a>  CCriticalSection::Unlock

リリース、`CCriticalSection`別のスレッドによって使用されるオブジェクト。

```
BOOL Unlock();
```

### <a name="return-value"></a>戻り値

0 以外の値、`CCriticalSection`オブジェクトがスレッドによって所有されているし、リリースが成功した。 それ以外の場合に 0 です。

### <a name="remarks"></a>Remarks

場合、`CCriticalSection`が使用されているスタンドアロン、`Unlock`クリティカル セクションによって制御されるリソースの使用を完了した直後に呼び出す必要があります。 場合、 [CSingleLock](../../mfc/reference/csinglelock-class.md)オブジェクトを使用している`CCriticalSection::Unlock`ロック オブジェクトのによって呼び出される`Unlock`メンバー関数。

### <a name="example"></a>例

  例をご覧ください[CCriticalSection::Lock](#lock)します。

## <a name="see-also"></a>関連項目

[CSyncObject クラス](../../mfc/reference/csyncobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CMutex クラス](../../mfc/reference/cmutex-class.md)
