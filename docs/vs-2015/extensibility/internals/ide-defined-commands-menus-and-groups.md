---
title: Команды, определенные в интегрированной среде разработки, меню и групп | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 32e8135328c11fd74311371d07645a525426371e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994203"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Команды, меню и группы, определенные в интегрированной среде разработки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Меню, команд и группы команд уже определены для использования [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среды разработки. Эти команды также доступны для использования при расширении [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="finding-environment-defined-commands"></a>Поиск команды, определенные в среде  
 Команды среды определяются в набор четырех vsct-файлы:  
  
- SharedCmdDef.vsct  
  
- SharedCmdPlace.vsct  
  
- ShellCmdDef.vsct  
  
- ShellCmdPlace.vsct  
  
  Эти файлы расположены в  *\<путь установки пакета SDK для Visual Studio >* \VisualStudioIntegration\Common\Inc\\. Эти файлы содержат определения идентификаторов GUID для меню и групп, которые можно использовать в в файле конфигурации (.vsct) таблицы команд вашего VSPackage как контейнеры для меню, группы и команды.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Идентификаторы GUID и идентификаторы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Предоставляет значения GUID и идентификатор меню в строке меню Visual Studio и групп, которые они содержат.  
  
 [Идентификаторы GUID и идентификаторы панелей инструментов Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Предоставляет значения GUID и идентификатор, панелей инструментов в Интегрированной среде разработки Visual Studio и групп, которые они содержат.  
  
 [Идентификаторы GUID и идентификаторы команд Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Предоставляет значения GUID и идентификатор команды, определенные в интегрированной среде разработки Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Visual Studio Command Table (. Файлы Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Команды, определенные в интегрированной среде разработки, для расширения систем проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
