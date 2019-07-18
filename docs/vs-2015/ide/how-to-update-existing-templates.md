---
title: Практическое руководство. Обновление существующих шаблонов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26482e844a4850efb1c50b15e51e4153baf1f9ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186271"
---
# <a name="how-to-update-existing-templates"></a>Практическое руководство. Обновление существующих шаблонов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

После создания шаблона и сжатия файлов в ZIP-файл может потребоваться изменить шаблон. Это можно сделать путем изменения файлов шаблона вручную или путем экспорта нового шаблона из проекта, основанного на шаблоне.  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Использование мастера экспорта шаблона для обновления существующего шаблона  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] предоставляет мастер **экспорта шаблона**, который можно использовать для обновления существующего шаблона.  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>Использование экспорта шаблона для обновления существующего шаблона  
  
1. В меню **Файл** последовательно выберите пункты **Создать** и **Новый проект**.  
  
2. Выберите шаблон, который требуется обновить, введите имя и расположение временного проекта и нажмите кнопку **ОК**.  
  
3. Измените этот проект в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. В меню **Файл** выберите **Экспорт шаблона** и используйте мастер **экспорта шаблона** для создания нового шаблона.  
  
5. После сжатия обновленного шаблона в ZIP-файл удалите ZIP-файл старого шаблона.  
  
## <a name="manually-updating-an-existing-template"></a>Обновление существующего шаблона вручную  
 Вы можете обновить существующий шаблон за пределами [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] путем изменения файлов в сжатом ZIP-файле.  
  
#### <a name="to-manually-update-an-existing-template"></a>Порядок обновления существующего шаблона вручную  
  
1. Найдите ZIP-файл, содержащий шаблон. По умолчанию этот файл расположен в папке \My Documents\Visual Studio *версия*\My Exported Templates\\.  
  
2. Извлеките ZIP-файл.  
  
3. Измените или удалите текущие файлы шаблона или добавьте в него новые файлы.  
  
4. Откройте, измените и сохраните VSTEMPLATE-файл с кодом XML для обработки обновленного поведения или новых файлов. Дополнительные сведения о схеме VSTEMPLATE см. в разделе [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md). Дополнительные сведения о том, что именно можно параметризовать в исходных файлах, см. в разделе [Параметры шаблона](../ide/template-parameters.md)  
  
5. Выберите файлы в шаблоне, щелкните правой кнопкой мыши, выберите пункт **Отправить**, а затем пункт **Сжатая ZIP-папка**. Выбранные файлы будут сжаты в ZIP-файл.  
  
6. Поместите новый ZIP-файл в тот же каталог, где находится старый ZIP-файл.  
  
7. Удалите извлеченные файлы шаблона и ZIP-файл старого шаблона.  
  
8. Запустите (с правами администратора) экземпляр командной строки разработчика (в меню "Пуск" в разделе **Visual Studio 2010/Инструменты Visual Studio/Командная строка разработчика** ).  
  
9. Выполните следующую команду: `devenv /installvstemplates`.  
  
## <a name="see-also"></a>См. также  
 [Настройка шаблонов](../ide/customizing-project-and-item-templates.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Параметры шаблона](../ide/template-parameters.md)   
 [Практическое руководство. создание начальных наборов](../ide/how-to-create-starter-kits.md)
