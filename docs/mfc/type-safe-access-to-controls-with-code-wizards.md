---
title: コード ウィザードを使用した、コントロールへのタイプ セーフ アクセス
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: fefa722209d37e2612201c4471e5764f9d71f27a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685036"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>コード ウィザードを使用した、コントロールへのタイプ セーフ アクセス

DDX 機能に慣れている場合は、[メンバー変数の追加ウィザード](../ide/add-member-variable-wizard.md)のコントロールプロパティを使用して、タイプセーフなアクセスを作成できます。 この方法は、コードウィザードを使用せずにコントロールを作成するよりも簡単です。

コントロールの値にアクセスするだけの場合は、DDX がそれを提供します。 コントロールの値にアクセスするよりも多くの操作を行う場合は、メンバー変数の追加ウィザードを使用して、適切なクラスのメンバー変数をダイアログクラスに追加します。 このメンバー変数をコントロールプロパティにアタッチします。

メンバー変数は、値プロパティではなく、コントロールプロパティを持つことができます。 Value プロパティは、コントロールから返されたデータの型 (`CString` や**int**など) を参照します。コントロールプロパティは、型が MFC のコントロールクラスの1つであるデータメンバー (`CButton` や `CEdit`など) を介してコントロールに直接アクセスできるようにします。

> [!NOTE]
>  特定のコントロールについては、必要に応じて、Value プロパティを持つ複数のメンバー変数と、Control プロパティを持つメンバー変数を1つだけ持つことができます。 コントロールにマップされている MFC オブジェクトは1つだけです。コントロールまたはその他のウィンドウに複数のオブジェクトがアタッチされていると、メッセージマップがあいまいになる可能性があります。

このオブジェクトを使用して、コントロールオブジェクトの任意のメンバー関数を呼び出すことができます。 このような呼び出しは、ダイアログボックスのコントロールに影響します。 たとえば、`CButton`型の変数*m_Checkbox*によって表されるチェックボックスコントロールの場合、次のようにを呼び出すことができます。

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

ここでは、メンバー変数*m_Checkbox*は、[コードウィザードを使用しないコントロールへのタイプセーフアクセス](../mfc/type-safe-access-to-controls-without-code-wizards.md)に示されているメンバー関数 `GetMyCheckbox` と同じ目的を果たします。 このチェックボックスが [自動] チェックボックスでない場合は、ボタンがクリックされたときに、BN_CLICKED コントロール通知メッセージのダイアログクラスのハンドラーが必要になります。

コントロールの詳細については、「[コントロール](../mfc/controls-mfc.md)」を参照してください。

## <a name="see-also"></a>参照

[ダイアログ ボックスのコントロールへのタイプ セーフ アクセス](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[MFC でのダイアログボックスの操作](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[コード ウィザードを使用しない、コントロールへのタイプ セーフ アクセス](../mfc/type-safe-access-to-controls-without-code-wizards.md)
