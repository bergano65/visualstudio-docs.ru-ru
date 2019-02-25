---
title: Команды, определенные в интегрированной среде разработки, для расширения систем проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26f5ee29a52546e7f2111189f54d64c160a94cea
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646920"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Команды, определенные в интегрированной среде разработки, для расширения систем проектов
Если вы хотите расширить системы проектов, можно использовать команды и команды, предоставляемые группы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки.

 В следующих разделах перечислены элементы команды, которые особенно полезны для расширения систем проектов.

## <a name="command-menus"></a>Команды меню
 В следующей таблице показаны команды меню, которые являются полезные расположений применить высокого уровня команды, которые вызывают расширитель проекта.

|Команда меню|Описание:|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|**Проекта** меню верхнего уровня.|
|IDM_VS_TOOL_PROJWIN|**Обозревателе решений** панели инструментов.|

## <a name="shortcut-menus"></a>Контекстные меню
 В следующей таблице показаны контекстные меню, которые применяются при выборе одного узла в **обозревателе решений**, или при наличии однородных множественный в **обозревателе решений**, когда это все выбранные узлы имеют тот же тип.

|Контекстное меню|Описание:|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Применяется, если выбран узел проекта.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Применяется, когда выбран файл.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Применяется, когда папка выбрана.|
|IDM_VS_CTXT_WEBREFFOLDER|Применяется при выборе папки веб-ссылки.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Применяется, когда выбран корневой узел ссылок с именем «Ссылки».|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Применяется, когда выбраны узлы ссылок на; к ним относятся, сборка, COM и только ссылки на проект. Не поддерживает веб-ссылки.|

 В следующей таблице показаны контекстные меню, которые применяются, когда выделение в **обозревателе решений** охватывает несколько иерархий

|Контекстное меню|Описание|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Применяется, если текущее выделение содержит узел решения и проекта корневые узлы.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Применяется, если текущее выделение содержит элементы узла и проект решения.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Применяется, если текущее выделение состоит только несколько узлов проекта корневой.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Применяется, если текущее выделение содержит сочетание корневых узлов проекта и элементов проектов. Кроме того выделение может содержать узел решения.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Применяется, если текущее выделение содержит элементы проекта из нескольких проектов в решении, или при выборе элементов различных типов в одном проекте.|

## <a name="command-groups"></a>Группы команд
 В следующей таблице показаны группы команд, которые можно использовать при расширении проекты, и для доступа к <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> контекстное меню.

|Группа команд|Описание:|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Команды для создания, повторного построения и развертывания проекта.|
|IDG_VS_CTXT_COMPILELINK|Команды для компиляции и компоновки проекта.|
|IDG_VS_CTXT_PROJECT_CONFIG|Команды, которые задают конфигурацию проекта и порядок построения.|
|IDG_VS_CTXT_PROJECT_ADD|Команды, добавление элементов в проект.|
|IDG_VS_CTXT_PROJECT_START|Команды, задайте стартовый проект, связанный с клавишу F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Команды для сохранения элементов проекта.|
|IDG_VS_CTXT_PROJECT_DEBUG|Команды для отладки.|
|IDG_VS_CTXT_PROJECT_SCC|Команды для управления версиями.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Команды вырезания, копирования и операции вставки.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Команды, которые предоставляют доступ к **свойства проекта** диалоговое окно.|

## <a name="see-also"></a>См. также
- [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Команды MenuCommand и OleMenuCommand](../../extensibility/menucommands-vs-olemenucommands.md)
- [Создание повторно используемых групп кнопок](../../extensibility/creating-reusable-groups-of-buttons.md)