---
title: プロジェクト ビルドの警告 PRJ0041
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: b0fceff05ffe35515965b7e0a880c8b4c941b07e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297724"
---
# <a name="project-build-warning-prj0041"></a>プロジェクト ビルドの警告 PRJ0041

見つかりませんファイル 'file' の依存関係の依存関係。 プロジェクトでは、ビルドすることが、このファイルが見つかるまで期限切れにします。

ファイル (リソース ファイルまたは.idl/.odl ファイル、たとえばに含まれている include ステートメントが、プロジェクト システムを解決できませんでした。

プロジェクト システムがプリプロセッサ ステートメント (たとえば #if) を処理できないため、問題が発生したステートメント実際にはできません、ビルドの一部。

この警告を解決するには、.rc ファイル内のすべての不要なコードを削除するか、適切な名前のプレース ホルダー ファイルを追加します。