---
title: Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865cf2ec43071a01a333961e118beab14abab82b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651896"
---
# <a name="autorecover-environment-options-dialog-box"></a>Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"

Эта страница диалогового окна **Параметры** служит для настройки автоматического резервного копирования файлов. Можно указать необходимость восстановления измененных файлов в случае неожиданного завершения работы Visual Studio.

Чтобы открыть это диалоговое окно, в меню **Сервис** выберите **Параметры**, а затем — **Среда** > **Автовосстановление**. Если эта страница отсутствует в списке, выберите **Показать все параметры** в диалоговом окне **Параметры**.

**Сохранять данные автовосстановления каждые [n] мин**

Используйте этот параметр, чтобы настроить периодичность автоматического сохранения файла в редакторе. Для ранее сохраненных файлов копия файла сохраняется в папке *%USERPROFILE%\Documents\Visual Studio \\[версия]\Backup Files\\[имя проекта]* . Если файл является новым и не был сохранен, он автоматически сохраняется с использованием случайного имени файла.

**Хранить данные автовосстановления [n] дн.**

Используйте этот параметр, чтобы указать период, в течение которого Visual Studio будет хранить файлы, созданные для автоматического восстановления.

### <a name="see-also"></a>См. также

- [Диалоговое окно "Параметры"](../../ide/reference/options-dialog-box-visual-studio.md)