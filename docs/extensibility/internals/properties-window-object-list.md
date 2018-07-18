---
title: Список объектов в окне Свойства | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6b7d238f7ce64122ac18a52dab59afb063ce47e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130140"
---
# <a name="properties-window-object-list"></a>Список объектов окна свойств
Список объектов в **свойства** окно является список раскрывающегося списка, который позволяет изменить выделение на другие объекты, доступные в один или несколько выбранных периодов. При выборе другой объект из этого списка инициирует вызов <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> для информирования среды, что был выбран новый объект. Информация, отображаемая в **свойства** окно затем изменяется для отображения свойства, связанные с вновь выделенный объект.  
  
## <a name="the-object-list"></a>Список объектов  
 Список объектов состоит из двух полей: имя объекта (отображается полужирным шрифтом) и тип объекта.  
  
 Имя объекта, отображается слева от типа объекта полужирным шрифтом извлекается из самого объекта с помощью `Name` свойства, предоставляемые <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> интерфейса. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, единственным способом на <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, возвращает <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> для компонентного класса этого интерфейса. **Свойства** окне используется <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> получить имя компонентного класса, который отображается как имя объекта в раскрывающемся списке.  
  
 Если объект не имеет `Name` свойство, имя не отображается в поле имени списка объектов. Свойство Name можно добавить в объект, если требуется, чтобы имя отображается в списке объектов.  
  
 Если COM-объект не реализует <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, **свойства** окне отображается имя интерфейса вместо имени объекта слева от списка.  
  
## <a name="see-also"></a>См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)