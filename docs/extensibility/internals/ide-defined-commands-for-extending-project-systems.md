---
title: "Команды, определенные в интегрированной среде разработки, для расширения системы проектов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8ef8f9d3bd75057708f7e1d380da83a38d7efb4b
ms.lasthandoff: 02/22/2017

---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Команды, определенные в интегрированной среде разработки, для расширения системы проектов
При необходимости расширение системы проектов, можно использовать команды и команду групп, предоставляемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки.  
  
 В следующих разделах перечислены элементы команды, которые особенно полезны для расширения системы проектов.  
  
## <a name="command-menus"></a>Команды меню  
 В следующей таблице показаны команды меню, которые представляют собой полезные место вставьте высокого уровня команды, которые вызывают расширения проекта.  
  
|Команда меню|Описание|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**Проекта** меню верхнего уровня.|  
|IDM_VS_TOOL_PROJWIN|**Обозревателе решений** инструментов.|  
  
## <a name="shortcut-menus"></a>Контекстные меню  
 В следующей таблице показаны контекстные меню, которые применяются при выборе одного узла в **обозревателе решений**, или при наличии однородных множественный в **обозреватель решений**, который лучше при всех выбранных узлов того же типа.  
  
|Контекстное меню|Описание|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Применяется, если выбран узел проекта.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Применяется, когда выбран файл.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Применяется, когда папка выбрана.|  
|IDM_VS_CTXT_WEBREFFOLDER|Применяется при выборе папки веб-ссылки.|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Применяется при выборе ссылки на корневой узел с именем «Ссылки».|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Применяется, если выбраны узлы ссылок; к ним относятся сборки, COM и только ссылки проекта. Не включает веб-ссылки.|  
  
 В следующей таблице показаны контекстные меню, которые применяются, когда значение в **обозревателе решений** охватывает несколько иерархий  
  
|Контекстное меню|Описание|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|Применяется, когда текущее выделение содержит узел решения и проекта корневые узлы.|  
|IDM_VS_CTXT_XPROJ_SLNITEM|Применяется, когда текущее выделение содержит узел и проект элементов решения.|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Применяется, когда текущее выделение состоит только несколько узлов проекта корневой.|  
|IDM_VS_CTXT_XPROJ_PROJITEM|Применяется, когда текущее выделение содержит сочетание корневых узлов проекта и элементов проекта. Кроме того выбор может содержать узел решения.|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|Применяется, когда текущее выделение содержит элементы проекта из нескольких проектов в решении, или при выборе элементов различных типов в одном проекте.|  
  
## <a name="command-groups"></a>Группы команд  
 В следующей таблице показаны группы команд, которые можно использовать, когда расширения проектов, и можно обращаться из <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>контекстное меню.</xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>  
  
|Группы команд|Описание|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|Команды для создания, повторного построения и развертывания проекта.|  
|IDG_VS_CTXT_COMPILELINK|Команды для компиляции и компоновки проекта.|  
|IDG_VS_CTXT_PROJECT_CONFIG|Команды, задать конфигурацию проекта и порядок построения.|  
|IDG_VS_CTXT_PROJECT_ADD|Команды, добавление элементов в проект.|  
|IDG_VS_CTXT_PROJECT_START|Команды, задание запускаемого проекта, связанного с клавишей F5.|  
|IDG_VS_CTXT_PROJECT_SAVE|Команды для сохранения элементов проекта.|  
|IDG_VS_CTXT_PROJECT_DEBUG|Команды для отладки.|  
|IDG_VS_CTXT_PROJECT_SCC|Команды для управления версиями.|  
|IDG_VS_CTXT_PROJECT_TRANSFER|Команды вырезания, копирования и операции вставки.|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|Команды, которые обеспечивают доступ к **свойства проекта** диалоговое окно.|  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Команды MenuCommand и OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Создание многократно используемых групп кнопок](../../extensibility/creating-reusable-groups-of-buttons.md)
