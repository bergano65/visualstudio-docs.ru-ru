---
title: Команды, меню и группы, определенные интегрированной средой разработки | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192737"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Команды, меню и группы, определенные в интегрированной среде разработки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Многие меню, команды и группы команд уже определены для использования [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной средой разработки. Эти команды также доступны для использования при расширении [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="finding-environment-defined-commands"></a>Поиск команд, определяемых средой  
 Команды среды определены в наборе из четырех vsct-файлов:  
  
- Шаредкмддеф. vsct  
  
- Шаредкмдплаце. vsct  
  
- Шеллкмддеф. vsct  
  
- Шеллкмдплаце. vsct  
  
  Эти файлы находятся в *\<Visual Studio SDK installation path>* \висуалстудиоинтегратион\коммон\инк \\ . Эти файлы содержат определения и идентификаторы GUID меню и групп, которые можно использовать в файле конфигурации командной таблицы (. vsct) пакета VSPackage в качестве контейнеров для собственных меню, групп и команд.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Идентификаторы GUID и идентификаторы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Предоставляет значения GUID и идентификатора меню в строке меню Visual Studio и содержащихся в них группах.  
  
 [Идентификаторы GUID и идентификаторы панелей инструментов Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Предоставляет идентификатор GUID и значения идентификатора панелей инструментов в интегрированной среде разработки Visual Studio и содержащихся в них групп.  
  
 [Идентификаторы GUID и идентификаторы команд Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Предоставляет идентификаторы GUID и ИДЕНТИФИКАТОРы команд, определенных интегрированной средой разработки Visual Studio.  
  
## <a name="see-also"></a>См. также:  
 [Командная таблица Visual Studio (. Vsct) файлы](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Команды, определяемые интегрированной средой разработки для расширения систем проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
