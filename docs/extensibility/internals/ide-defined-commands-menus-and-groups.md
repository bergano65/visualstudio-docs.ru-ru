---
title: "Команды, определенные в интегрированной среде разработки, меню и групп | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 032baaa57dd91cb07eac547da810d16e708f0828
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ide-defined-commands-menus-and-groups"></a>Команды, определенные в интегрированной среде разработки, меню и групп
Меню, команд и группах команд уже определены для использования [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки. Эти команды также доступны для использования при расширении [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="finding-environment-defined-commands"></a>Поиск команд, определенных в среде  
 В набор четыре vsct-файлами определены команды среды:  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Эти файлы расположены в  *\<путь установки Visual Studio SDK >*\VisualStudioIntegration\Common\Inc\\. Эти файлы предоставляют определения и идентификаторы GUID меню и групп, которые можно использовать в в файле конфигурации (.vsct) таблицы команд вашего VSPackage как контейнеры для меню, группы и команды.  
  
## <a name="in-this-section"></a>Содержание  
 [Идентификаторы GUID и идентификаторы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Предоставляет значения GUID и ID меню в строке меню Visual Studio и групп, которые они содержат.  
  
 [Идентификаторы GUID и идентификаторы панелей инструментов Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Предоставляет значения GUID и ID панелей инструментов в Интегрированной среде разработки Visual Studio и групп, которые они содержат.  
  
 [Идентификаторы GUID и идентификаторы команд Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Предоставляет значения GUID и ID команд, определенных в Интегрированной среде разработки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Таблицы команд Visual Studio (. Файлы Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Команды, определенные в интегрированной среде разработки, для расширения системы проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)