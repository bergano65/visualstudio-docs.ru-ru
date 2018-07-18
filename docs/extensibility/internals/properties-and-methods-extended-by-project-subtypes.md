---
title: Свойства и методы расширенной подтипов проекта | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23510ffbb42e0c0c37c07e0ee80ae15f99e5df00
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132095"
---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Свойства и методы расширенной подтипов проекта
Подтип проекта имеет большое количество электроэнергии, чтобы влиять на поведение проекта, так как оно создается как инвентаризации программного обеспечения из базового проекта. В этом разделе описаны некоторые возможности, которые расширенный или изменить подтипов проекта.  
  
## <a name="features-gained-by-aggregation"></a>За счет статистической функции  
 В следующей таблице перечислены многие методы статистической обработки позволяют подтипы проекта для переопределения базового проектах.  
  
|Методы переопределены статистической обработки|Подтип проекта|  
|---------------------------------------|---------------------|  
|Из <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Включает подтипом проекта для<br /><br /> -Измените заголовок и значок для узла проекта.<br />-Полностью переопределить проекта `Browse` объекта.<br />-Управления, возможно ли переименование проекта.<br />-Порядок сортировки элемент управления.<br />-Элемент управления пользовательский контекст, чтобы получить динамическую справку.|  
|Из <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Позволяет подтипом проекта контролировать, какие контекстные службы предоставляются для конструкторов и редакторов.|  
|Из <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Включает подтипом проекта для<br /><br /> -Участвовать в маршрутизации команд для проекта команды.<br />-Добавлять, удалять или отключать внешней команды проекта и активные команды в обозревателе решений.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Включает подтипом проекта для фильтрации, пользователь видит в **Добавление нового элемента** диалоговое окно.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Включает подтипом проекта для<br /><br /> -Определите генератор по умолчанию, заданного расширения файла.<br />-Сопоставьте имя человека генератор для чтения на COM-объект.|  
  
## <a name="properties-used-by-project-subtypes"></a>Свойства, используемые для подтипов проекта  
 Система проектов среды и базовым можно использовать свойства из <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID> и <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> перечислений, рассмотренных в следующей таблице, чтобы включить подтипом проекта для управления различными функциями системы проектов.  
  
|Свойство VSHPROPID|Подтип проекта|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Позволяет подтипом проекта для управления содержимым **добавить элемент** диалоговое окно. Подтипом проекта можно предоставить новой спецификации шаблона каталогов, добавления новых типов элементов, удалите существующие элементы и реорганизовать подмножество элементов базового проекта **добавить элемент** диалоговое окно.|  
|`PropertyPagesCLSIDList`|Позволяет подтипом проекта для добавления или удаления страницы свойств зависят от конфигурации.|  
|`CfgPropertyPagesCLSIDList`|Позволяет подтипом проекта для добавления или удаления страниц свойств в зависимости от конфигурации.|  
|`ExtObjectCATID`|Позволяет подтипом проекта для предоставления автоматизированного расширителя для проекта или проекта объектов элементов узнав CATID расширения. Например, подтип проекта может предоставить пользовательский `Project.Extender("<subtype>")` объекта.|  
|`BrowseObjectCATID`|Позволяет подтипом проекта для предоставления автоматизированного расширителя для `Browse` объекта узнав CATID расширения. Например, подтип проекта можно добавить дополнительные свойства для <xref:EnvDTE.Project.Properties%2A> коллекции.|  
|`CfgBrowseObjectCATID`|Позволяет подтипом проекта для предоставления автоматизированного расширителя для обзора объект конфигурации проекта. Например, подтип проекта можно добавить дополнительные свойства для <xref:EnvDTE.Configuration.Properties%2A> коллекции.|  
|`CfgExtObjectCATID`|Позволяет подтипом проекта для предоставления автоматизированного расширителя для объекта конфигурации.|  
|`DefaultPlatformName`|Позволяет подтипом проекта для определения имени платформы для объектов конфигурации проекта.|  
  
 Базовый проект предоставляет реализацию по умолчанию выше свойств. Получает базовый проект с помощью вызова `QueryInterface` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> для подтипа внешней проекта, позволяя тем самым подтип для переопределения реализации свойств проекта.  
  
## <a name="see-also"></a>См. также  
 [Разработка подтипов проекта](../../extensibility/internals/project-subtypes-design.md)