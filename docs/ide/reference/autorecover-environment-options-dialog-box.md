---
title: "Страница &quot;Автовосстановление&quot;, папка &quot;Среда&quot;, диалоговое окно &quot;Параметры&quot; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 320b31b01237656be157be9ad9ce5787521215db
ms.contentlocale: ru-ru
ms.lasthandoff: 05/24/2017

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
