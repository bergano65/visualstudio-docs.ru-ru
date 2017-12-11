---
title: "Практическое руководство. Обновление существующих шаблонов | Документы Майкрософт"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0fffcc55953e394c5efd00b86949f04474a66111
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-update-existing-templates"></a>Практическое руководство. Обновление существующих шаблонов
После создания шаблона и сжатия файлов в ZIP-файл может потребоваться изменить шаблон. Это можно сделать путем изменения файлов шаблона вручную или путем экспорта нового шаблона из проекта, основанного на шаблоне.  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Использование мастера экспорта шаблонов для обновления существующего шаблона  
Visual Studio предоставляет мастер **экспорта шаблонов**, который можно использовать для обновления существующего шаблона.  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>Использование экспорта шаблона для обновления существующего шаблона  
  
1.  Откройте диалоговое окно **Новый проект**, а затем выберите **Файл**, **Создать**, **Проект**.  
  
2.  Выберите шаблон, который требуется обновить, введите имя и расположение проекта и нажмите кнопку **ОК**.  
  
3.  Измените проект в Visual Studio.  
  
4.  В меню **Проект** выберите команду **Экспорт шаблона**.  

    Открывается **мастер экспорта шаблонов**.  

5.  Следуйте указаниям мастера, чтобы экспортировать шаблон в виде ZIP-файла.  

6.  Удалите старый ZIP-файл шаблона.  
  
## <a name="manually-updating-an-existing-template"></a>Обновление существующего шаблона вручную  
Вы можете обновить существующий шаблон за пределами Visual Studio, изменив файлы в сжатом ZIP-файле.  
  
#### <a name="to-manually-update-an-existing-template"></a>Порядок обновления существующего шаблона вручную  
  
1.  Найдите ZIP-файл, содержащий шаблон. По умолчанию этот файл находится в папке %USERPROFILE%\Documents\Visual Studio \<версия\>\My Exported Templates\..  
  
2.  Извлеките ZIP-файл.  
  
3.  Измените или удалите текущие файлы шаблона или добавьте в него новые файлы.  
  
4.  Откройте, измените и сохраните VSTEMPLATE-файл с кодом XML для обработки обновленного поведения или новых файлов.  

    Дополнительные сведения о схеме VSTEMPLATE см. в разделе [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md). Дополнительные сведения о том, что именно можно параметризовать в исходных файлах, см. в разделе [Параметры шаблона](../ide/template-parameters.md).  
  
5.  Выберите файлы в шаблоне, щелкните правой кнопкой мыши, выберите пункт **Отправить**, а затем пункт **Сжатая ZIP-папка**.  

    Выбранные файлы будут сжаты в ZIP-файл.  
  
6.  Поместите новый ZIP-файл в тот же каталог, где находится старый ZIP-файл.  
  
7.  Удалите извлеченные файлы шаблона и ZIP-файл старого шаблона.  
  
8.  Запустите экземпляр командной строки разработчика с повышенными привилегиями:  

  1. В меню "Пуск" выберите **Visual Studio \<версия\>**, **Командная строка разработчика**.  

  2. В контекстном меню выберите **Дополнительно**, **Запуск от имени администратора**.  
  
9. Выполните следующую команду: `devenv /installvstemplates`.  
  
## <a name="see-also"></a>См. также  
[Настройка шаблонов](../ide/customizing-project-and-item-templates.md)   
[Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
[Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
[Параметры шаблона](../ide/template-parameters.md)   
[Практическое руководство. Создание начальных наборов](../ide/how-to-create-starter-kits.md)