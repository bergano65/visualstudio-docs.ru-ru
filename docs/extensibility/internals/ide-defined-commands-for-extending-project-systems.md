---
title: "Команды, определенные в интегрированной среде разработки, для расширения системы проектов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5e6f4caf8466100763b6a4ae11f6760a3d4c655
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Команды, определенные в интегрированной среде разработки, для расширения системы проектов
Если вы хотите расширить системы проектов, можно использовать команды и команды, предоставляемые группами [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки.  
  
 В следующих разделах перечислены элементы команды, которые особенно полезны для расширения системы проектов.  
  
## <a name="command-menus"></a>Команды меню  
 В следующей таблице показаны команды меню, которые являются полезным расположения вводить высокого уровня команды, вызывающие расширения проекта.  
  
|Команда меню|Описание|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**Проекта** меню верхнего уровня.|  
|IDM_VS_TOOL_PROJWIN|**Обозревателе решений** инструментов.|  
  
## <a name="shortcut-menus"></a>Контекстные меню  
 В следующей таблице показаны контекстные меню, которые применяются, когда выбран один узел **обозревателе решений**, или если существует несколько однородных вариантов выбора в **обозревателе решений**, является, если все выбранные узлы имеют тот же тип.  
  
|Контекстное меню|Описание|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Применяется, если выбран узел проекта.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Применяется, когда выбран файл.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Применяется, когда папка выбрана.|  
|IDM_VS_CTXT_WEBREFFOLDER|Применяется при выборе папки веб-ссылки.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Применяется, когда выбран корневой узел ссылки с именем «Ссылки».|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Применяется при выборе узлов ссылок; к ним относятся сборки, COM и только ссылки на проект. Не включает веб-ссылки.|  
  
 В следующей таблице показаны контекстные меню, которые применяются, когда выделение в **обозревателе решений** охватывает несколько иерархий  
  
|Контекстное меню|Описание|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Применяется, когда текущее выделение содержит узел решения и проекта корневые узлы.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Применяется, когда текущее выделение содержит элементы узла и проектом решения.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Применяется, когда текущее выделение состоит только несколько узлов проекта корневой.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Применяется, когда текущее выделение содержит сочетание корневых узлов проекта и элементов проектов. Кроме того Выбор могут содержать узел решения.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Применяется, когда текущее выделение содержит элементы проекта из нескольких проектов в решении или при выборе элементов различных типов в одном проекте.|  
  
## <a name="command-groups"></a>Группы команд  
 В следующей таблице показаны группы команд, которые можно использовать при расширять проекты, и можно обращаться из <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> контекстное меню.  
  
|Группа команд|Описание|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Команды для создания, повторного построения и развертывания проекта.|  
|IDG_VS_CTXT_COMPILELINK|Команды для компиляции и компоновки проекта.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Команды, которые можно задать конфигурацию проекта и порядок построения.|  
|IDG_VS_CTXT_PROJECT_ADD|Команды, добавление элементов в проект.|  
|IDG_VS_CTXT_PROJECT_START|Команды, которые задание запускаемого проекта, связанного с клавишей F5.|  
|IDG_VS_CTXT_PROJECT_SAVE|Команды для сохранения элементов проекта.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Команды для отладки.|  
|IDG_VS_CTXT_PROJECT_SCC|Команды для системы управления версиями.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Команды вырезания, копирования и операции вставки.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Команды, которые обеспечивают доступ к **свойства проекта** диалоговое окно.|  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Команды MenuCommand и OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Создание повторно используемых групп кнопок](../../extensibility/creating-reusable-groups-of-buttons.md)