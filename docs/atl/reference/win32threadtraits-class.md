---
title: Win32ThreadTraits クラス
ms.date: 11/04/2016
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
ms.openlocfilehash: d086a42f5dcdf005d10c8853776da66b691a8e11
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495473"
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits クラス

このクラスは、Windows スレッドの作成関数を提供します。 スレッドが CRT 関数を使用しない場合は、このクラスを使用します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class Win32ThreadTraits
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[Win32ThreadTraits:: CreateThread](#createthread)|雑音CRT 関数を使用しないスレッドを作成するには、この関数を呼び出します。|

## <a name="remarks"></a>Remarks

スレッド特性は、特定の種類のスレッドに対して作成関数を提供するクラスです。 作成関数には、Windows の[CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)関数と同じシグネチャとセマンティクスがあります。

スレッドの特徴は、次のクラスによって使用されます。

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

スレッドが CRT 関数を使用する場合は、代わりに[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)を使用します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase. h

##  <a name="createthread"></a>Win32ThreadTraits:: CreateThread

CRT 関数を使用しないスレッドを作成するには、この関数を呼び出します。

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

この関数は`CreateThread` 、を呼び出してスレッドを作成します。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
