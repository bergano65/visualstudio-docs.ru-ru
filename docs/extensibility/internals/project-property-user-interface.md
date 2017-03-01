---
title: "Проект пользовательского интерфейса свойств | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 16
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: b344731061053abb208225a0480408ebbe682050
ms.lasthandoff: 02/22/2017

---
# <a name="project-property-user-interface"></a>Пользовательский интерфейс свойства проекта
Элементы подтипом проекта можно использовать в проекте **страницы свойств** диалоговое окно, как они предоставляются по базовый проект скрыть сделать элементы управления только для чтения и всей страницы, передаваемой или добавить страницы подтипа проекта для **страницы свойств** диалоговое окно.  
  
## <a name="extending-the-project-property-dialog-box"></a>Расширение диалоговое окно свойств проекта  
 Подтип проект реализует расширителей автоматизации и Обзор объектов конфигурации проекта. Эти расширения реализуют <xref:EnvDTE.IFilterProperties>интерфейс для определенного свойства скрытые или только для чтения.</xref:EnvDTE.IFilterProperties> **Страницы свойств** диалоговое окно базовый проект, реализуемый базовый проект учитывает фильтрации выполняемых расширителей автоматизации.  
  
 Процесс расширения **свойство проекта** диалоговое окно, приведенным ниже:  
  
-   Базовый проект получает расширителей из подтип проекта путем реализации <xref:EnvDTE80.IInternalExtenderProvider>интерфейса.</xref:EnvDTE80.IInternalExtenderProvider> Обзор, автоматизации проектов и конфигурации проекта: Обзор объектов базового проекта все реализовывать этот интерфейс.  
  
-   Реализация <xref:EnvDTE80.IInternalExtenderProvider>для обзора проекта и объектов автоматизации проекта делегировать <xref:EnvDTE80.IInternalExtenderProvider>реализацию агрегатора подтип проекта (то есть они `QueryInterface` для <xref:EnvDTE80.IInternalExtenderProvider>на <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>объект проекта).</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider>  
  
-   Объект конфигурации обзора базовый проект также реализует <xref:EnvDTE80.IInternalExtenderProvider>для подключения непосредственно в расширитель автоматизации из объекта конфигурации проекта подтип.</xref:EnvDTE80.IInternalExtenderProvider> Его реализация делегирует <xref:EnvDTE80.IInternalExtenderProvider>интерфейс, реализуемый агрегатора подтип проекта.</xref:EnvDTE80.IInternalExtenderProvider>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, реализуемый объекта Обзор конфигурации проекта, возвращает <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>объекта.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, также реализован объект Обзор конфигурации проекта, возвращает <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>объекта.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>  
  
-   Подтип проекта можно определить соответствующие идентификаторы CATID для различных объектов являются расширяемыми базового проекта во время выполнения путем получения следующие <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>значения:</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 Чтобы определить идентификаторы CATID для области проекта, подтипом проекта извлекает выше свойства <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>из `VSITEMID``typedef`.</xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> Подтип проекта также может потребоваться указать, какие **страницы свойств** страницах диалогового окна отображаются для проекта, зависят от конфигурации и конфигурации независимо. Некоторые подтипы проекта может потребоваться удалить встроенные страницы и добавить проект подтип определенных страниц. Чтобы включить этот проект управляемый клиент вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>метод для следующих свойств:</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>  
  
-   `VSHPROPID_PropertyPagesCLSIDList`— Список разделенных точкой с запятой CLSID страниц свойств зависят от конфигурации.  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`Список разделенных точкой с запятой CLSID страниц свойств в зависимости от конфигурации.  
  
 Поскольку проект подтипа агрегаты <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>объекта, его можно переопределить определении этих свойств, чтобы указать, какие **страницы свойств** отображаются диалоговые.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Подтип проекта можно загрузить эти свойства из внутреннего базовый проект и затем добавить или удалить CLSID при необходимости.  
  
 Новые страницы свойств, добавленных с подтипом проекта передаются объекту конфигурации проекта от реализации базового проекта. Обзор объекта конфигурации проекта поддерживает расширителей автоматизации. Дополнительные сведения о AutomationExtenders см. в разделе [реализация и использование расширителей автоматизации](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Страницы свойств, реализуемый вызова подтип проекта <xref:EnvDTE.Project.Extender%2A>для извлечения собственные проекта подтип конфигурации Обзор объекта, расширяет объект Обзор конфигурации базового проекта.</xref:EnvDTE.Project.Extender%2A>  
  
## <a name="see-also"></a>См. также  
 <xref:EnvDTE.IFilterProperties></xref:EnvDTE.IFilterProperties>   
 [Страницы свойств-диалоговое окно](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
