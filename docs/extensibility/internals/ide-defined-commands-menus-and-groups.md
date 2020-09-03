---
title: Команды, меню и группы, определенные интегрированной средой разработки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6557f49b019a6793698dabe852919ec2e9f28cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707719"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Команды, меню и группы, определенные в интегрированной среде разработки
Многие меню, команды и группы команд уже определены для использования [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной средой разработки. Эти команды также доступны для использования при расширении [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="finding-environment-defined-commands"></a>Поиск команд, определяемых средой
 Команды среды определены в наборе из четырех vsct-файлов:

- Шаредкмддеф. vsct

- Шаредкмдплаце. vsct

- Шеллкмддеф. vsct

- Шеллкмдплаце. vsct

  Эти файлы находятся в *\<Visual Studio SDK installation path>* \висуалстудиоинтегратион\коммон\инк \\ . Эти файлы содержат определения и идентификаторы GUID меню и групп, которые можно использовать в файле конфигурации командной таблицы (. vsct) пакета VSPackage в качестве контейнеров для собственных меню, групп и команд.

## <a name="in-this-section"></a>в этом разделе
- [Идентификаторы GUID и идентификаторы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Предоставляет значения GUID и идентификатора меню в строке меню Visual Studio и содержащихся в них группах.

- [Идентификаторы GUID и идентификаторы панелей инструментов Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Предоставляет идентификатор GUID и значения идентификатора панелей инструментов в интегрированной среде разработки Visual Studio и содержащихся в них групп.

- [Идентификаторы GUID и идентификаторы команд Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Предоставляет идентификаторы GUID и ИДЕНТИФИКАТОРы команд, определенных интегрированной средой разработки Visual Studio.

## <a name="see-also"></a>См. также раздел
- [Файлы таблицы команд Visual Studio (VSCT-файлы)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Команды, определенные в интегрированной среде разработки, для расширения систем проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
