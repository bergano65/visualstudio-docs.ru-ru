---
title: Страница "Язык интерфейса", папка "Среда", диалоговое окно "Параметры"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
- VS.ToolsOptionsPag.Environment.International_Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afb07a7cbc591c30ebbe7b281b49b38bfb0c911e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944792"
---
# <a name="international-settings-environment-options-dialog-box"></a>Страница "Язык интерфейса", папка "Среда", диалоговое окно "Параметры"
На странице «Выбор языка» можно изменить язык по умолчанию, если на компьютере установлено несколько языковых версий интегрированной среды разработки (IDE). Чтобы открыть это диалоговое окно, выберите **Параметры** в меню **Сервис**, а затем выберите **Выбор языка** в папке **Среда**. Если эта страница отсутствует в списке, выберите **Показать все параметры** в диалоговом окне **Параметры**.

> [!NOTE]
> Доступные в диалоговых окнах параметры, а также названия и расположение команд меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).


 **Язык** Содержит список доступных языков для языковых версий установленного продукта. Этот параметр недоступен, если на компьютере не установлено несколько языковых версий. Если среда разработки является общей для продуктов на разных языках, язык меняется на **такой же, как в Microsoft Windows**.

> [!CAUTION]
> В системе с несколькими установленными языками средства построения Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe и связанные файлы) не зависят от этого параметра. Эти средства используют версию для последнего установленного языка. Средства для ранее установленных языков перезаписываются, так как средства сборки Visual C++ не используют модель вспомогательных библиотек DLL.


## <a name="see-also"></a>См. также

- [Установка языковых пакетов](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
- [Диалоговое окно "Параметры среды"](../../ide/reference/environment-options-dialog-box.md)