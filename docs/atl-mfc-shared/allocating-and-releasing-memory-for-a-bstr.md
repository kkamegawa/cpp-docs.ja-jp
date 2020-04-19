---
title: BSTR 用のメモリの割り当てと解放
ms.date: 11/04/2016
f1_keywords:
- bstr
helpviewer_keywords:
- BSTRs, memory allocation
- memory deallocation, string memory
- memory [C++], releasing
- memory allocation, BSTRs
- memory deallocation, BSTR memory
- strings [C++], releasing
ms.assetid: 98041e29-3442-4a02-b425-7a4a13e9cc84
ms.openlocfilehash: a7a82acff959d18dcadd3a2c8516a20d60a617d3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491409"
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>BSTR 用のメモリの割り当てと解放

を作成`BSTR`して COM オブジェクト間で渡す場合は、メモリリークを回避するために、使用しているメモリを十分に扱う必要があります。 が`BSTR`インターフェイス内に保持されている場合は、操作が完了したら、そのメモリを解放する必要があります。 ただし、が`BSTR`インターフェイスから渡されると、受信側のオブジェクトはそのメモリの管理に責任を持ちます。

一般に、に`BSTR`割り当てられたメモリの割り当てと解放の規則は次のとおりです。

- `BSTR`引数を必要とする関数を呼び出す場合は、呼び出しの前にのメモリ`BSTR`を割り当ててから、後で解放する必要があります。 例えば:

   [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]

- を返す`BSTR`関数を呼び出す場合は、自分で文字列を解放する必要があります。 例えば:

   [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]

- を返す`BSTR`関数を実装する場合は、文字列を割り当てますが、その文字列は解放されません。 関数を受け取ると、メモリが解放されます。 例えば:

   [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]

## <a name="see-also"></a>関連項目

[文字列 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)<br/>
[SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring)<br/>
[SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)
