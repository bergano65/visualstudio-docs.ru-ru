---
title: Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed5ad6259ede32304cfe15ef4e79c6b3e56dbd9d
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143311"
---
# <a name="autorecover-environment-options-dialog-box"></a>Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"

Эта страница диалогового окна **Параметры** служит для настройки автоматического резервного копирования файлов. Здесь также можно указать необходимость восстановления измененных файлов в случае неожиданного завершения работы Visual Studio.

Чтобы открыть это диалоговое окно, в меню **Сервис** выберите **Параметры**, а затем — **Среда** > **Автовосстановление**. Если эта страница отсутствует в списке, выберите **Показать все параметры** в диалоговом окне **Параметры**.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

**Сохранять данные автовосстановления каждые [n] мин**

Используйте этот параметр, чтобы настроить периодичность автоматического сохранения файла в редакторе. Для ранее сохраненных файлов копия файла сохраняется в папке *%USERPROFILE%\Documents\Visual Studio \<версия>\Backup Files\\<projectname>*. Если файл является новым и не был сохранен, он автоматически сохраняется с использованием случайного имени файла.

**Хранить данные автовосстановления [n] дн.**

Используйте этот параметр, чтобы указать период, в течение которого Visual Studio будет хранить файлы, созданные для автоматического восстановления.

## <a name="see-also"></a>См. также

- [Диалоговое окно "Параметры"](../../ide/reference/options-dialog-box-visual-studio.md)