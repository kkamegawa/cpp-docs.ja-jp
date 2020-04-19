---
title: CRTThreadTraits クラス
ms.date: 11/04/2016
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
ms.openlocfilehash: 9e12e64041e38b8fa014815870132a75885014bf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496563"
---
# <a name="crtthreadtraits-class"></a>CRTThreadTraits クラス

このクラスは、CRT スレッドの作成関数を提供します。 スレッドが CRT 関数を使用する場合は、このクラスを使用します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CRTThreadTraits
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CRTThreadTraits:: CreateThread](#createthread)|雑音CRT 関数を使用できるスレッドを作成するには、この関数を呼び出します。|

## <a name="remarks"></a>Remarks

スレッド特性は、特定の種類のスレッドに対して作成関数を提供するクラスです。 作成関数には、Windows の[CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)関数と同じシグネチャとセマンティクスがあります。

スレッドの特徴は、次のクラスによって使用されます。

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

スレッドが CRT 関数を使用しない場合は、代わりに[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)を使用します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase. h

##  <a name="createthread"></a>  CRTThreadTraits::CreateThread

CRT 関数を使用できるスレッドを作成するには、この関数を呼び出します。

```
static HANDLE CreateThread(
    LPSECURITY_ATTRIBUTES lpsa,
    DWORD dwStackSize,
    LPTHREAD_START_ROUTINE pfnThreadProc,
    void* pvParam,
    DWORD dwCreationFlags,
    DWORD* pdwThreadId) throw();
```

### <a name="parameters"></a>パラメーター

*lpsa*<br/>
新しいスレッドのセキュリティ属性。

*dwStackSize*<br/>
新しいスレッドのスタックサイズ。

*pfnThreadProc*<br/>
新しいスレッドのスレッドプロシージャ。

*pvParam*<br/>
スレッドプロシージャに渡されるパラメーター。

*Dwのフラグ*<br/>
作成フラグ (0 または CREATE_SUSPENDED)。

*pdwThreadId*<br/>
入出力成功した場合は、新しく作成されたスレッドのスレッド ID を受け取る DWORD 変数のアドレス。

### <a name="return-value"></a>戻り値

新しく作成されたスレッドへのハンドル、または失敗した場合は NULL を返します。 エラーの詳細情報を取得するには、 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してください。

### <a name="remarks"></a>Remarks

この関数のパラメーターの詳細については、「 [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) 」を参照してください。

この関数は、 [_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)を呼び出してスレッドを作成します。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
