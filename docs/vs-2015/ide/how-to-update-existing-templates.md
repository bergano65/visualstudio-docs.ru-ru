---
title: 'Практическое: обновление существующих шаблонов | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item templates, updating existing templates
- Visual Studio templates, updating existing templates
- project templates, updating existing templates
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c5d091e58904cae058c5a2a5ade1b8ceec4c738
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561068"
---
# <a name="how-to-update-existing-templates"></a>Практическое руководство. Обновление существующих шаблонов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: обновление существующих шаблонов](https://docs.microsoft.com/visualstudio/ide/how-to-update-existing-templates).  
  
После создания шаблона и сжатия файлов в ZIP-файл может потребоваться изменить шаблон. Это можно сделать путем изменения файлов шаблона вручную или путем экспорта нового шаблона из проекта, основанного на шаблоне.  
  
## <a name="using-the-export-template-wizard-to-update-an-existing-template"></a>Использование мастера экспорта шаблона для обновления существующего шаблона  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] предоставляет **Экспорт шаблона** мастер, который может использоваться для обновления существующего шаблона.  
  
#### <a name="to-use-export-template-to-update-an-existing-template"></a>Использование экспорта шаблона для обновления существующего шаблона  
  
1.  В меню **Файл** последовательно выберите пункты **Создать** и **Новый проект**.  
  
2.  Выберите шаблон, который требуется обновить, введите имя и расположение временного проекта и нажмите кнопку **ОК**.  
  
3.  Измените этот проект в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  На **файл** меню, щелкните **Экспорт шаблона**и использовать **Экспорт шаблона** мастер, чтобы создать новый шаблон.  
  
5.  После сжатия обновленного шаблона в ZIP-файл удалите ZIP-файл старого шаблона.  
  
## <a name="manually-updating-an-existing-template"></a>Обновление существующего шаблона вручную  
 Вы можете обновить существующий шаблон за пределами [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] путем изменения файлов в сжатом ZIP-файле.  
  
#### <a name="to-manually-update-an-existing-template"></a>Порядок обновления существующего шаблона вручную  
  
1.  Найдите ZIP-файл, содержащий шаблон. По умолчанию этот файл находится в Мои \My Documents\Visual Studio *версии*\My Exported Templates\\.  
  
2.  Извлеките ZIP-файл.  
  
3.  Измените или удалите текущие файлы шаблона или добавьте в него новые файлы.  
  
4.  Откройте, измените и сохраните VSTEMPLATE-файл с кодом XML для обработки обновленного поведения или новых файлов. Дополнительные сведения о схеме VSTEMPLATE см. в разделе [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md). Дополнительные сведения о можно параметризовать в исходных файлах, см. в разделе [параметров шаблона](../ide/template-parameters.md)  
  
5.  Выберите файлы в шаблоне, щелкните правой кнопкой мыши, нажмите кнопку **отправить**, а затем нажмите кнопку **сжатых ZIP-папку**. Выбранные файлы будут сжаты в ZIP-файл.  
  
6.  Поместите новый ZIP-файл в тот же каталог, где находится старый ZIP-файл.  
  
7.  Удалите извлеченные файлы шаблона и ZIP-файл старого шаблона.  
  
8.  Запустить (с правами администратора) экземпляр из командной строки разработчика (в меню «Пуск» в разделе **Visual Studio 2010 или Visual Studio Tools/Командная строка разработчика**).  
  
9. Выполните следующую команду: `devenv /installvstemplates`.  
  
## <a name="see-also"></a>См. также  
 [Настройка шаблонов](../ide/customizing-project-and-item-templates.md)   
 [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)   
 [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Параметры шаблона](../ide/template-parameters.md)   
 [Практическое руководство. Создание начальных наборов](../ide/how-to-create-starter-kits.md)



