---
title: Команды, определенные в интегрированной среде разработки, меню и групп | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b65266ad3367df5cebeabc251bc8bceb6cda7075
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129393"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Команды, определенные в интегрированной среде разработки, меню и групп
Меню, команд и группах команд уже определены для использования [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки. Эти команды также доступны для использования при расширении [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="finding-environment-defined-commands"></a>Поиск команд, определенных в среде  
 В набор четыре vsct-файлами определены команды среды:  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Эти файлы расположены в  *\<путь установки Visual Studio SDK >* \VisualStudioIntegration\Common\Inc\\. Эти файлы предоставляют определения и идентификаторы GUID меню и групп, которые можно использовать в в файле конфигурации (.vsct) таблицы команд вашего VSPackage как контейнеры для меню, группы и команды.  
  
## <a name="in-this-section"></a>В этом разделе  
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