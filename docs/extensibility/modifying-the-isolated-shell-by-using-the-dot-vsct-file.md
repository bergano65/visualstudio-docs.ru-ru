---
title: "Изменение с помощью изолированной оболочки. Файл Vsct | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: a20b546c6e8d6d70a17d3d0bae575a5b2898d781
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Изменение с помощью изолированной оболочки. Файл Vsct
Проект пользовательского интерфейса для проекта изолированной оболочки Visual Studio содержит файл .vsct, который позволяет указать, какие группы приложений и отдельных команд доступны в приложении. Ниже приведен отрывок из файла .vsct без изменений.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 По умолчанию включены большинство команд и группы команд. Чтобы исключить команды или группы команд, просто раскомментируйте этой команды или группы.  
  
 Например, чтобы удалить область следующего и предыдущего панели команд, раскомментируйте `No_PaneNextPaneCommand` и `No_PanePrevPaneCommand` записи:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Подробный пример эти настройки, см. в разделе [Пошаговое руководство: создание простого приложения изолированной оболочки](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Файлы, на которые имеются ссылки  
 Файл .vsct по умолчанию для приложения ссылается на следующие файлы. Эти файлы расположены в подкаталоге \VisualStudioIntegration\Common\Inc\ каталога установки Visual Studio SDK.  
  
|Файл|Описание|  
|----------|-----------------|  
|wbids.h|Удостоверения пользовательского интерфейса для веб-Обзор пакета.|  
|AppIDCmdUsed.vsct|Таблица команда для основных элементов пользовательского интерфейса Visual Studio.|  
|EmulatorCmdUsed.vsct|Таблица команда для Emacs и краткое описание элементов пользовательского интерфейса редактора эмуляции.|  
|Vsdebugguids.h|Определяет идентификаторы GUID, команды, параметры страницы и другие функции отладчика Visual Studio.|  
|VsDbgCmdUsed.vsct|Таблица команд отладчика.|  
  
 Файл AppIDCmdUsed.vsct содержит элементы пользовательского интерфейса Visual Studio, основанные на символы, определенные в файле .vsct.  
  
 Дополнительные сведения см. в разделе [проектирование таблицы команд XML (. Файлы Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) и [Справочник по схемам VSCT XML](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>См. также  
 [Visual Studio изолированной оболочки](../extensibility/visual-studio-isolated-shell.md)
