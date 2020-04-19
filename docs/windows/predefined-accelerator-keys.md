---
title: アクセラレータ キー (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator
helpviewer_keywords:
- accelerator keys
- keyboard shortcuts
- keyboard shortcuts [C++], predefined
- menus [C++], shortcut keys
- keyboard shortcuts [C++], menu association
ms.assetid: f234c5f2-4ec3-4c9e-834a-b5dd297625b9
ms.openlocfilehash: bb407538f254df5f187ff91b85a8eaa753a52287
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362388"
---
# <a name="accelerator-keys-c"></a>アクセラレータ キー (C++)

## <a name="predefined-accelerator-keys"></a>定義済みのアクセラレータ キー

Windows アプリケーション プロジェクトの一部として使用できるいくつかの定義済みのアクセラレータ キーがあります。 これらの仮想キーの一部は、Windows 環境用です。 他のユーザーは、ブラウザーや Unicode アプリケーションをサポートします。 どのアクセラレータでもこれらのキーを使用できます。

|キー|説明|
|---------|-----------------|
|VK_ACCEPT|(IME) を受け入れる|
|VK_BROWSER_BACK|(Windows)ブラウザー、**戻る**キー|
|VK_BROWSER_FAVORITES|(Windows)ブラウザー、**お気に入り**キー|
|VK_BROWSER_FORWARD|(Windows)ブラウザー、**フォワード**キー|
|VK_BROWSER_HOME|(Windows)ブラウザー、**開始**と**ホーム**キー|
|VK_BROWSER_REFRESH|(Windows)ブラウザー、**更新**キー|
|VK_BROWSER_SEARCH|(Windows)ブラウザー、**検索**キー|
|VK_BROWSER_STOP|(Windows)ブラウザー、**停止**キー|
|VK_CONVERT|(IME) 変換|
|VK_FINAL|(IME) final モード|
|VK_HANGUEL|(IME)ハングル モード (VK_HANGUL を使用して互換性の維持)|
|VK_HANGUL|(IME)ハングル モード|
|VK_HANJA|(IME)Hanja モード|
|VK_JUNJA|(IME)Junja モード|
|VK_KANA|(IME)かなモード|
|VK_KANJI|(IME)漢字モード|
|VK_LAUNCH_APP1|(Windows)**スタート アプリケーション 1**キー|
|VK_LAUNCH_APP2|(Windows)**アプリケーション 2 の開始**キー|
|VK_LAUNCH_MAIL|(Windows)**メールの起動**キー|
|VK_LAUNCH_MEDIA_SELECT|(Windows)**メディアの選択**キー|
|VK_LCONTROL|**左 Ctrl**キー|
|VK_LMENU|**左側のメニュー**キー|
|VK_LSHIFT|**左シフト**キー|
|VK_MEDIA_NEXT_TRACK|(Windows)**次のトラック**キー|
|VK_MEDIA_PLAY_PAUSE|(Windows)**メディアの再生/一時停止**キー|
|VK_MEDIA_PREV_TRACK|(Windows)**前のトラック**キー|
|VK_MEDIA_STOP|(Windows)**メディアの停止**キー|
|VK_MODECHANGE|(IME) モードの変更要求|
|VK_NONCONVERT|(IME) 無変換|
|VK_OEM_1|(Windows)米国標準キーボードの **;:** キー|
|VK_OEM_102|(Windows)山かっこキーまたは RT 102 key キーボードの円記号キー|
|VK_OEM_2|(Windows)米国標準キーボードの **/でしょうか。** key|
|VK_OEM_3|(Windows)米国標準キーボードの **`~** キー|
|VK_OEM_4|(Windows)米国標準キーボードの **[{** キー|
|VK_OEM_5|(Windows)米国標準キーボードの **\\ &#124;** キー|
|VK_OEM_6|(Windows)米国標準キーボードの **]}** キー|
|VK_OEM_7|(Windows)米国標準キーボードの"1 つの引用符と二重引用符"キー|
|VK_OEM_COMMA|(Windows)すべての国/地域、 **、** キー|
|VK_OEM_MINUS|(Windows)すべての国/地域、 **-** キー|
|VK_OEM_PERIOD|(Windows)すべての国/地域、**します。** key|
|VK_OEM_PLUS|(Windows)すべての国/地域、 **+** キー|
|VK_PACKET|(Windows)キーストロークである場合に、Unicode 文字を渡すために使用します。|
|VK_RCONTROL|**右 Ctrl**キー|
|VK_RMENU|**右側のメニュー**キー|
|VK_RSHIFT|**右シフト**キー|
|VK_SLEEP|**コンピューターのスリープ**キー|
|VK_VOLUME_DOWN|(Windows)**Volume Down**キー|
|VK_VOLUME_MUTE|(Windows)**音量ミュート**キー|
|VK_VOLUME_UP|(Windows)**Volume Up**キー|
|VK_XBUTTON1|(Windows)**X1**マウスのボタン|
|VK_XBUTTON2|(Windows)**X2**マウスのボタン|

## <a name="accelerator-key-association"></a>アクセラレータ キーの関連付け

メニュー項目とキーボードの組み合わせで同じプログラム コマンドを発行したいと思うことはよくあります。 メニュー項目と、アプリケーションのアクセラレータ テーブル内のエントリには、同じリソース識別子 (ID) を割り当てることでは、このアクションを実行します。 次に、メニュー項目のキャプションを編集して、アクセラレータの名前を表示します。 メニュー項目とアクセラレータ キーの詳細については、次を参照してください。[メニュー コマンド](../windows/associating-a-menu-command-with-an-accelerator-key.md)します。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[アクセラレータ エディター](../windows/accelerator-editor.md)<br/>