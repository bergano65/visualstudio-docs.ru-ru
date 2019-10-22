---
title: Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры" | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 743543e03806a842eabc2bbfc69011d63b1264d0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660967"
---
# <a name="autorecover-environment-options-dialog-box"></a>Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Эта страница диалогового окна "Параметры" служит для настройки автоматического резервного копирования файлов. Кроме того, на этой странице можно указать, следует ли восстанавливать измененные файлы после непредвиденного завершения работы интегрированной среды разработки (IDE). Чтобы открыть это диалоговое окно, выберите **Параметры** в меню **Сервис**, а затем выберите **Автовосстановление** в папке **Среда**. Если эта страница отсутствует в списке, выберите **Показать все параметры** в диалоговом окне **Параметры**.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, в меню "Сервис" выберите команду "Импорт и экспорт параметров". Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **Сохранять данные автовосстановления каждые \<n> минут** Используйте этот параметр, чтобы настроить периодичность автоматического сохранения файла в редакторе. Для ранее сохраненных файлов копия файла сохранятся в папке \\...\My Documents\Visual Studio \<*версия*>\Backup Files\\<*имя_проекта*>. Если файл является новым и не был ранее сохранен вручную, он автоматически сохраняется с использованием случайного имени файла.

 **Хранить данные автовосстановления \<n> дн.** Используйте этот параметр, чтобы указать период, в течение которого Visual Studio будет хранить файлы, созданные для автоматического восстановления.

## <a name="see-also"></a>См. также раздел
 [Диалоговое окно "Параметры"](../../ide/reference/options-dialog-box-visual-studio.md)
