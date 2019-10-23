---
title: Страница "Язык интерфейса", папка "Среда", диалоговое окно "Параметры"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e55c0e81877c2735571705a2b2d2529b0fa3a74
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666994"
---
# <a name="options-dialog-box-environment--international-settings"></a>Диалоговое окно "Параметры": Страница "Выбор языка" \> папка "Среда"

На странице "Выбор языка" можно изменить язык по умолчанию, если на компьютере установлено несколько языковых версий интегрированной среды разработки (IDE). Чтобы открыть это диалоговое окно, выберите **Параметры** в меню **Сервис**, а затем выберите **Выбор языка** в папке **Среда**.

**Язык**

Содержит список доступных языков для языковых версий установленного продукта. Если среда разработки является общей для продуктов на разных языках, язык меняется на **такой же, как в Microsoft Windows**.

> [!CAUTION]
> В системе с несколькими установленными языками средства построения Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe и связанные файлы) не зависят от этого параметра. Эти средства используют версию для последнего установленного языка. Средства для ранее установленных языков перезаписываются, так как средства сборки Visual C++ не используют модель вспомогательных библиотек DLL.

### <a name="see-also"></a>См. также

- [Установка языковых пакетов](../../install/install-visual-studio.md#step-6---install-language-packs-optional)