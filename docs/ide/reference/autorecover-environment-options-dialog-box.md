---
title: Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры" | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 45a85b1acde8933b3baae6abf1847de3e36d7eff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="autorecover-environment-options-dialog-box"></a>Страница "Автовосстановление", папка "Среда", диалоговое окно "Параметры"
Эта страница диалогового окна "Параметры" служит для настройки автоматического резервного копирования файлов. Кроме того, на этой странице можно указать, следует ли восстанавливать измененные файлы после непредвиденного завершения работы интегрированной среды разработки (IDE). Чтобы открыть это диалоговое окно, выберите **Параметры** в меню **Сервис**, а затем выберите **Автовосстановление** в папке **Среда**. Если эта страница отсутствует в списке, выберите **Показать все параметры** в диалоговом окне **Параметры**.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, в меню "Сервис" выберите команду "Импорт и экспорт параметров". Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
 **Автосохранение каждые \<n> мин.**  
 Используйте этот параметр, чтобы настроить периодичность автоматического сохранения файла в редакторе. Для ранее сохраненных файлов копия файла сохранятся в папке \\...\My Documents\Visual Studio \<*версия*>\Backup Files\\<*имя_проекта*>. Если файл является новым и не был ранее сохранен вручную, он автоматически сохраняется с использованием случайного имени файла.  
  
 **Хранить данные автовосстановления \<n> дн.**  
 Используйте этот параметр, чтобы указать период, в течение которого Visual Studio будет хранить файлы, созданные для автоматического восстановления.  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно "Параметры"](../../ide/reference/options-dialog-box-visual-studio.md)