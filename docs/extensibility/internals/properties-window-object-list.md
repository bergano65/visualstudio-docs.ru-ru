---
title: "Список объектов окна свойств | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Окно свойств, список объектов"
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Список объектов окна свойств
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Список объекта в **Свойства** окно раскрывающийся список, который позволяет изменить выделение на другие объекты доступными в один или несколько выбранных окна.  Выбор другой объект из этого списка, чтобы активировать вызов <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> уведомить среду, что новый объект был установлен.  Сведения, отображаемые в **Свойства** окно затем изменить, чтобы указать свойства, связанные с вновь выделенным объектом.  
  
## Список объектов  
 Список объекта состоит из 2 полей: имя объекта, выделенный полужирным шрифтом \(\) и типом объекта.  
  
 Имя объекта отображается слева от типа объекта, выделенные полужирным шрифтом извлекается из самого объекта с помощью `Name` защищенное свойство  <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> интерфейс.  <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>единственный метод  <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>возвращает  <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> для компонентного класса этого интерфейса.  **Свойства** окно использует  <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> получить имя coclass, который отображается в качестве имени объекта в раскрывающемся списке.  
  
 Если объект не имеет a `Name` свойство имя не отображается в области имени списка объектов.  Можно добавить свойство имени объекта, если требуется имя, отображаемое в списке объектов.  
  
 Если COM\-объект не реализует <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>"  **Свойства** окно отображает имя интерфейса вместо имен объектов в левой части списка.  
  
## См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)