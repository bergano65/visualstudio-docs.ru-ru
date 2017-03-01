---
title: "Свойства и методы дополнено подтипы проектов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 17
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
ms.openlocfilehash: 38bb86636edeaeda4485b7ebe6c8a6349450343c
ms.lasthandoff: 02/22/2017

---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Свойства и методы дополнено подтипы проектов
Подтип проекта имеет большое количество электроэнергии, чтобы влиять на поведение проекта, поскольку он формируется как агрегатор базовый проект. В этом разделе содержатся сведения о некоторых функций, расширенный или изменено подтипы проектов.  
  
## <a name="features-gained-by-aggregation"></a>За счет статистической функции  
 В следующей таблице приведены многие из методов статистической обработки позволяет подтипы проектов для переопределения в базовый проектов.  
  
|Методы переопределены статистической обработки|Подтип проекта|  
|---------------------------------------|---------------------|  
|Из <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Позволяет подтип для проекта<br /><br /> -Измените заголовок и значок для узла проекта.<br />-Полностью переопределить проекта `Browse` объекта.<br />-Управление, возможно ли переименование проекта.<br />-Управление порядком сортировки.<br />-Элемент управления пользовательский контекст, чтобы получить динамическую справку.|  
|Из <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Позволяет подтипом проекта контролировать, какие контекстные службы предоставляются для конструкторов и редакторов.|  
|Из <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Позволяет подтип для проекта<br /><br /> -Участвовать в маршрутизации команд для проекта команд.<br />-Добавить, удалить или отключить внешней команды проекта и активные команды в обозревателе решений.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2></xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Подтип для фильтрации, пользователь видит в проект позволяет **Add New Item** диалоговое окно.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Позволяет подтип для проекта<br /><br /> -Определите файлу присваивается расширение генератор данных по умолчанию.<br />-Сопоставьте имя человека генератор для чтения на COM-объект.|  
  
## <a name="properties-used-by-project-subtypes"></a>Свойства, используемые подтипы проектов  
 Система проектов среды и базовым можно использовать свойства из <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>и <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>перечисления, рассмотренных в следующей таблице, чтобы включить подтипом проекта для управления различными функциями системы проектов.</xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> </xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>  
  
|Свойство VSHPROPID|Подтип проекта|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Позволяет подтипом проекта для управления содержимым **добавить элемент** диалоговое окно. Подтипом проекта можно предоставить новой спецификации шаблона каталогов, добавления новых типов элементов, удалите существующие элементы и реорганизовать подмножество элементов в базовый проект **добавить элемент** диалоговое окно.|  
|`PropertyPagesCLSIDList`|Позволяет подтипом проекта для добавления или удаления страниц свойств зависят от конфигурации.|  
|`CfgPropertyPagesCLSIDList`|Позволяет подтипом проекта для добавления или удаления страниц свойств в зависимости от конфигурации.|  
|`ExtObjectCATID`|Позволяет подтипом проекта для предоставления расширения автоматизации для проекта или проекта объектов элементов зная идентификатор CATID расширителя. Например, подтипом проекта можно предоставить пользовательский `Project.Extender("<subtype>")` объекта.|  
|`BrowseObjectCATID`|Позволяет подтипом проекта для предоставления расширения автоматизации для `Browse` объекта, зная идентификатор CATID расширителя. Например, подтип проект можно добавить дополнительные свойства для <xref:EnvDTE.Project.Properties%2A>коллекции.</xref:EnvDTE.Project.Properties%2A>|  
|`CfgBrowseObjectCATID`|Позволяет подтипом проекта для предоставления расширения автоматизации для обзора объект конфигурации проекта. Например, подтип проект можно добавить дополнительные свойства для <xref:EnvDTE.Configuration.Properties%2A>коллекции.</xref:EnvDTE.Configuration.Properties%2A>|  
|`CfgExtObjectCATID`|Позволяет подтипом проекта для предоставления расширения автоматизации для объекта конфигурации.|  
|`DefaultPlatformName`|Позволяет подтипом проекта определить имя платформы для объектов конфигурации проекта.|  
  
 Базовый проект предоставляет реализацию по умолчанию выше свойства. Базовый проект получает эти путем вызова `QueryInterface` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>для подтипа внешней проекта, позволяя подтипом проекта для переопределения реализации свойств.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
## <a name="see-also"></a>См. также  
 [Подтипы разработки проекта](../../extensibility/internals/project-subtypes-design.md)
