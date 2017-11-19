---
title: "Пользовательский интерфейс свойства проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 36d8f6afebf09d4efd176ba204dcc6f485a56124
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="project-property-user-interface"></a>Пользовательский интерфейс свойства проекта
Элементы подтипом проекта можно использовать в проекте **страницы свойств** диалоговое окно как они предоставляются по базовый проект скрыть сделать доступным только для чтения элементы управления и целые страницы, указанное или добавить проект подтипа страниц **Страницы свойств** диалоговое окно.  
  
## <a name="extending-the-project-property-dialog-box"></a>Расширение диалоговое окно свойств проекта  
 Подтип проекта реализует расширения автоматизации и Обзор объектов конфигурации проекта. Реализации этих расширений <xref:EnvDTE.IFilterProperties> интерфейс, чтобы конкретные свойства скрытые или только для чтения. **Страницы свойств** диалоговое окно базовый проект, реализуемый базовый проект учитывает фильтрация выполняется путем расширения автоматизации.  
  
 Процесс расширения **свойство проекта** диалоговое окно, описанные ниже:  
  
-   Базовый проект извлекает расширителей с подтипом проекта путем реализации <xref:EnvDTE80.IInternalExtenderProvider> интерфейса. Обзор, автоматизации проектов и конфигурации проекта: Обзор объектов базового проекта все реализация этого интерфейса.  
  
-   Реализация <xref:EnvDTE80.IInternalExtenderProvider> для обзора проекта и объектов автоматизации проекта делегировать <xref:EnvDTE80.IInternalExtenderProvider> реализацию агрегатора подтип проекта (то есть они `QueryInterface` для <xref:EnvDTE80.IInternalExtenderProvider> на <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объект проекта).  
  
-   Обзор объект конфигурации базового проекта также реализует <xref:EnvDTE80.IInternalExtenderProvider> для подключения непосредственно в автоматизированного расширителя из объекта конфигурации подтип проекта. Его реализация делегирует <xref:EnvDTE80.IInternalExtenderProvider> интерфейс, реализованный с помощью средства инвентаризации подтип проекта.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, реализуемый объекта обзора конфигурации проекта, возвращает <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объекта.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, также реализован объект обзора конфигурации проекта, возвращает <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> объекта.  
  
-   Подтип проекта можно определить соответствующие CATID для различных объектов являются расширяемыми базового проекта во время выполнения путем получения следующих <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> значения:  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 Чтобы определить CATID для области проекта, подтипом проекта получит выше свойства <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> из `VSITEMID``typedef`. Подтип проекта также может потребоваться указать, какие **страницы свойств** страницах диалогового окна отображаются для проектов, зависят от конфигурации и конфигурации независимо. Некоторые подтипы проекта может потребоваться удалить встроенные страницы и добавьте проект подтип отдельных страниц. Чтобы включить это управляемый клиент вызывает метод проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> метод для следующих свойств:  
  
-   `VSHPROPID_PropertyPagesCLSIDList`— Список разделенных точкой с запятой CLSID страниц свойств зависят от конфигурации.  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`Разделенный точками с запятой список идентификаторов CLSID страниц свойств в зависимости от конфигурации.  
  
 Так как проект подтипа агрегаты <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> объекта, его можно переопределить эти свойства, чтобы контролировать, какие **страницы свойств** диалоговое окно. Подтип проекта можно получить из внутреннего базового проекта эти свойства и затем добавить или удалить CLSID при необходимости.  
  
 Новые страницы свойств, добавленных с подтипом проекта передаются объект обзора конфигурации проекта от реализации базового проекта. Обзор объекта конфигурации проекта поддерживает автоматизированным расширителям. Дополнительные сведения о AutomationExtenders см. в разделе [реализация и использование расширения автоматизации](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Страницы свойств, реализуемый вызов подтип проекта <xref:EnvDTE.Project.Extender%2A> для получения собственных проекта подтип обзора объект конфигурации, расширяющий объект обзора конфигурации базового проекта.  
  
## <a name="see-also"></a>См. также  
 <xref:EnvDTE.IFilterProperties>   
 [Диалоговое окно страниц свойств](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)