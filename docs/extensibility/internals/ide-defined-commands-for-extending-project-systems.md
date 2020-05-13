---
title: IDE-Определенные команды для расширения проектных систем (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c0b2924548f50ad650389e3ad81759be1986a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707735"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Команды, определенные в интегрированной среде разработки, для расширения систем проектов
При расширении проектных систем можно использовать команды и командные группы, предоставляемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

 В следующих разделах перечисляются элементы команд, которые особенно полезны для расширения проектных систем.

## <a name="command-menus"></a>Меню командования
 В следующей таблице показаны меню команд, которые являются полезными для размещения команд высокого уровня, которые вызывают расширитель проекта.

|Меню командования|Описание|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|Меню верхнего уровня **проекта.**|
|IDM_VS_TOOL_PROJWIN|Панель инструментов **Solution Explorer.**|

## <a name="shortcut-menus"></a>Контекстные меню
 В следующей таблице показаны меню ярлыка, которые применяются при выборе одного узла в **Solution Explorer**или при наличии нескольких однородных выделений в **Solution Explorer,** когда все выбранные узлы имеют один и тот же тип.

|Меню ярлыка|Описание|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Применяется при выборе узла проекта.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Применяется при выборе файла.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Применяется при выборе папки.|
|IDM_VS_CTXT_WEBREFFOLDER|Применяется при выборе папки Web-справки.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Применяется при выборе корневого узла ссылок под названием "Ссылки".|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Применяется при выборе эталонных узлов; они включают только ссылки на сборку, COM и проект. Не содержит веб-ссылок.|

 В следующей таблице показаны меню ярлыков, которые применяются, когда выбор в **Solution Explorer** охватывает несколько иерархий,

|Меню ярлыка|Описание|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Применяется, когда текущий выбор содержит узлы раствора и корневые узлы проекта.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Применяется, когда текущий выбор содержит узла раствора и элементы проекта.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Применяется, когда текущий выбор состоит только из нескольких корневых узлов проекта.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Применяется, когда текущий выбор содержит сочетание корневых узлов проекта и элементов проекта. Кроме того, в выделении может содержаться узла раствора.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Применяется, когда текущий выбор содержит элементы проекта из нескольких проектов в решении, или когда элементы разных типов выбраны в одном проекте.|

## <a name="command-groups"></a>Командные группы
 В следующей таблице показаны группы команд, которые можно использовать при <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> расширении проектов, и что вы можете получить доступ через меню ярлыка.

|Командная группа|Описание|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Команды по созданию, восстановлению и развертыванию проекта.|
|IDG_VS_CTXT_COMPILELINK|Команды для компиляции и увязки проекта.|
|IDG_VS_CTXT_PROJECT_CONFIG|Команды, которые устанавливают конфигурацию проекта и строят порядок.|
|IDG_VS_CTXT_PROJECT_ADD|Команды, добавляющие элементы в проект.|
|IDG_VS_CTXT_PROJECT_START|Команды, которые устанавливают проект запуска, связанный с ключом F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Команды для сохранения элементов проекта.|
|IDG_VS_CTXT_PROJECT_DEBUG|Команды для отладки.|
|IDG_VS_CTXT_PROJECT_SCC|Команды для управления исходным источником.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Команды для операций по вырезу, копированию и вставке.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Команды, предоставляющие доступ к диалоговому окне **Project Properties.**|

## <a name="see-also"></a>См. также

- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Создание повторно используемых групп кнопок](../../extensibility/creating-reusable-groups-of-buttons.md)
