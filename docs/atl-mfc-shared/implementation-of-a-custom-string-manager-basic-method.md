---
title: カスタム文字列マネージャー (基本メソッド) の実装
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
ms.openlocfilehash: 92c1c46f5251980f9cefb55e052e9aff395e0e60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491311"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>カスタム文字列マネージャー (基本メソッド) の実装

文字列データのメモリ割り当てスキームをカスタマイズする最も簡単な方法は、ATL に用意さ`CAtlStringMgr`れているクラスを使用することですが、独自のメモリ割り当てルーチンを提供することです。 のコンストラクターは`CAtlStringMgr` 、1つのパラメーター ( `IAtlMemMgr`オブジェクトへのポインター) を受け取ります。 `IAtlMemMgr`は、ヒープへのジェネリックインターフェイスを提供する抽象基本クラスです。 では`CAtlStringMgr` 、インターフェイスを使用して、文字列データの格納に使用されるメモリの割り当て、再割り当て、解放を行います。 `IAtlMemMgr` `IAtlMemMgr`インターフェイスを自分で実装するか、ATL に用意されている5つのメモリマネージャークラスのいずれかを使用することができます。 ATL に用意されているメモリマネージャーは、単純に既存のメモリ割り当て機能をラップします。

- [Ccrtheap](../atl/reference/ccrtheap-class.md)標準 CRT ヒープ関数 ([malloc](../c-runtime-library/reference/malloc.md)、 [free](../c-runtime-library/reference/free.md)、および[realloc](../c-runtime-library/reference/realloc.md)) をラップします。

- [CWin32Heap](../atl/reference/cwin32heap-class.md)[HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc)、 [heapfree](/windows/win32/api/heapapi/nf-heapapi-heapfree)、および[heapfree](/windows/win32/api/heapapi/nf-heapapi-heaprealloc)を使用して、Win32 ヒープハンドルをラップします。

- [Clocalheap](../atl/reference/clocalheap-class.md)Win32 Api をラップします。[LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)、 [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree)、および[localrealloc](/windows/win32/api/winbase/nf-winbase-localrealloc)

- [Cglobalheap](../atl/reference/cglobalheap-class.md)Win32 Api をラップします。[GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)、 [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)、および[globalrealloc](/windows/win32/api/winbase/nf-winbase-globalrealloc)。

- [CComHeap](../atl/reference/ccomheap-class.md)COM タスクアロケーター Api をラップします。[CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc)、 [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)、 [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

文字列メモリ管理のために、最も役に立つクラスは`CWin32Heap` 、複数の独立したヒープを作成できることです。 たとえば、文字列に対してのみ個別のヒープを使用する場合は、次のようにします。

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

このプライベート文字列マネージャーを使用して`CString`変数のメモリを管理するには、 `CString`変数のコンストラクターにパラメーターとしてマネージャーへのポインターを渡します。

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>関連項目

[CStringT によるメモリ管理](../atl-mfc-shared/memory-management-with-cstringt.md)
