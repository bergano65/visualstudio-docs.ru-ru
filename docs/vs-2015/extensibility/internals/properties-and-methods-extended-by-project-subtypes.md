---
title: Свойства и методы, расширенные подтипами проектов | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f74f1f4a88fb01e09b30e7987f1bcec1d450571a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765129"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Свойства и методы, расширенные подтипами проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Подтип проекта имеет широкие возможности, чтобы влиять на поведение проекта, так как оно создается в качестве агрегатора базового проекта. В этом разделе перечислены некоторые функции, которые может расширенного или изменено с подтипов проекта.  
  
## <a name="features-gained-by-aggregation"></a>Функции, за счет статистической обработки  
 В следующей таблице перечислены многие методы, которые статистическая обработка позволяет выполнять подтипов проекта для переопределения в базовых проектов.  
  
|Методы переопределены статистической обработки|Подтип проекта|  
|---------------------------------------|---------------------|  
|Из <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Разрешает подтипу проекта<br /><br /> -Измените заголовок и значок для узла проекта.<br />-Полностью переопределить проекта `Browse` объекта.<br />-Элемент управления, возможно ли переименование проекта.<br />-Порядок сортировки элемент управления.<br />-Контекст пользователя control для динамической справки.|  
|Из <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Позволяет подтипом проекта, чтобы контролировать, какие контекстно-зависимые службы предоставляются для конструкторов и редакторов.|  
|Из <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Разрешает подтипу проекта<br /><br /> -Участвуете в маршрутизации команд для команды для проекта.<br />— Добавление, удаление или отключение команды окружения для проекта и активных команд в обозревателе решений.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Разрешает подтипу проекта для фильтрации, что пользователь видит в **Добавление нового элемента** диалоговое окно.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Разрешает подтипу проекта<br /><br /> -Определите файлу присваивается расширение генератора по умолчанию.<br />-Сопоставьте имя человека генератор для чтения на COM-объект.|  
  
## <a name="properties-used-by-project-subtypes"></a>Свойства, используемые подтипов проекта  
 Система проектов среды и базовым можно использовать свойства из <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> и <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> перечислений, рассмотренных в следующей таблице, чтобы включить подтипом проекта, для управления различными функциями системы проектов.  
  
|Свойство VSHPROPID|Подтип проекта|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Позволяет подтипом проекта, для управления содержимым **Добавление элемента** диалоговое окно. Подтипа проекта можно предоставить новую спецификацию каталогов шаблон, добавьте новые виды элементов, удалите существующие элементы и реорганизовать подмножество элементов базового проекта **Добавление элемента** диалоговое окно.|  
|`PropertyPagesCLSIDList`|Позволяет подтипом проекта, для добавления или удаления страниц свойств, независимых от конфигурации.|  
|`CfgPropertyPagesCLSIDList`|Позволяет подтипом проекта, для добавления или удаления страниц свойств, зависимых от конфигурации.|  
|`ExtObjectCATID`|Позволяет подтипом проекта, чтобы предоставить расширитель автоматизации для проекта или проект объектов элементов зная идентификатор CATID расширителя. Например, подтип проекта можно указать пользовательское `Project.Extender("<subtype>")` объекта.|  
|`BrowseObjectCATID`|Позволяет подтипом проекта, чтобы предоставить расширитель автоматизации для `Browse` объекта, зная идентификатор CATID расширителя. Например, подтип проекта можно добавить дополнительные свойства для <xref:EnvDTE.Project.Properties%2A> коллекции.|  
|`CfgBrowseObjectCATID`|Позволяет подтипом проекта, чтобы предоставить расширитель автоматизации для объекта просмотра конфигурации проекта. Например, подтип проекта можно добавить дополнительные свойства для <xref:EnvDTE.Configuration.Properties%2A> коллекции.|  
|`CfgExtObjectCATID`|Позволяет подтипом проекта, чтобы предоставить расширитель автоматизации для объекта конфигурации.|  
|`DefaultPlatformName`|Позволяет подтипом проекта определить имя платформы для объектов конфигурации проекта.|  
  
 Базовый проект предоставляет стандартную реализацию перечисленных свойств. Базовый проект получает их путем вызова `QueryInterface` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> для подтипа внешний проект, таким образом позволяя подтипом проекта, чтобы переопределить реализацию свойств.  
  
## <a name="see-also"></a>См. также  
 [Разработка подтипов проекта](../../extensibility/internals/project-subtypes-design.md)

