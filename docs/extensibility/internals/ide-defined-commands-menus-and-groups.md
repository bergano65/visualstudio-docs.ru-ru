---
title: "Команды, определенные в интегрированной среде разработки, меню и групп | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "команды, определенные в среде"
  - "vsct-файлах, константы, определенные в среде"
  - "группы команд, определенных в среде"
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# Команды, определенные в интегрированной среде разработки, меню и групп
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Меню, команд и группы команды уже определены для использования [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки. Эти команды также доступны для использования при расширении [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Поиск команды, определенные в среде  
 В набор четырех vsct\-файлах определены команды среды:  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Эти файлы расположены в *\< путь установки Visual Studio SDK \>*\\VisualStudioIntegration\\Common\\Inc\\. Эти файлы предоставляют определения и идентификаторы GUID меню и группы, которые можно использовать в файле конфигурации \(.vsct\) таблицы команды VSPackage как контейнеры, для меню, групп и команд.  
  
## Содержание  
 [Идентификаторы GUID и идентификаторы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Предоставляет значения GUID и идентификатор меню в строке меню Visual Studio и групп, которые они содержат.  
  
 [GUID и идентификаторы панелей инструментов Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Предоставляет значения GUID и идентификатор панелей инструментов в Интегрированной среде разработки Visual Studio и групп, которые они содержат.  
  
 [GUID и идентификаторы команд Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Предоставляет значения GUID и идентификатор команды, заданные в интегрированной среде разработки Visual Studio.  
  
## См. также  
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Команды, определенные в интегрированной среде разработки, для расширения системы проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)