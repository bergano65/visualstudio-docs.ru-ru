---
title: IDE-Определенные команды, меню и группы Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707719"
---
# <a name="ide-defined-commands-menus-and-groups"></a>Команды, меню и группы, определенные в интегрированной среде разработки
Многие меню, команды и группы команд уже [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] определены для использования IDE. Эти команды также доступны для использования [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]при расширении.

## <a name="finding-environment-defined-commands"></a>Поиск экологически хотековых команд
 Команды среды определяются в наборе из четырех файлов .vsct:

- SharedCmdDef.vsct

- SharedCmdPlace.vsct

- ShellCmdDef.vsct

- ShellCmdPlace.vsct

  Эти файлы расположены в\\ * \<Visual Studio SDK путь установки>*«VisualStudioIntegration»Common.Inc . Эти файлы предоставляют определения и GUID меню и группы, которые можно использовать в конфигурации командной таблицы (.vsct) файлв вашего VSPackage в качестве контейнеров для ваших собственных меню, групп и команд.

## <a name="in-this-section"></a>В этом разделе
- [Идентификаторы GUID и идентификаторы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Дает значения GUID и ID меню в панели меню Visual Studio и групп, которые они содержат.

- [Идентификаторы GUID и идентификаторы панелей инструментов Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Дает значения GUID и ID инструментов в Visual Studio IDE, а также групп, которые они содержат.

- [Идентификаторы GUID и идентификаторы команд Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Дает значения GUID и ID команд, определенные Visual Studio IDE.

## <a name="see-also"></a>См. также
- [Файлы таблицы команд Visual Studio (VSCT-файлы)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Команды, определенные в интегрированной среде разработки, для расширения систем проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
