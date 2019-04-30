---
title: Список объектов окна свойств | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eccc7cfc432918a80723251a7b9a87ec4e13450d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909094"
---
# <a name="properties-window-object-list"></a>Список объектов окна свойств
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Список объектов в **свойства** окно является список раскрывающегося списка, который позволяет изменить выделение на другие объекты, доступные в один или несколько выбранных периодов. Выбрав другой объект из этого списка запускает вызов <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> сообщать среде, что был выбран новый объект. Информация, отображаемая в **свойства** окно затем изменяется для отображения свойства, связанные с вновь выбранный объект.  
  
## <a name="the-object-list"></a>Список объектов  
 Список объектов состоит из двух полей: имя объекта (отображается полужирным шрифтом) и тип объекта.  
  
 Имя объекта, который отображается слева от типа объекта полужирным шрифтом, извлекается из самого объекта с помощью `Name` свойства, предоставляемые <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> интерфейс. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, единственный метод на <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, возвращает <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> для компонентного класса этот интерфейс. **Свойства** использует окно <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> получить имя компонентного класса, которое отображается как имя объекта в раскрывающемся списке.  
  
 Если объект не имеет `Name` свойство, имя не отображается в области имя списка объектов. Свойство Name можно добавить к объекту, если вы хотите, чтобы имя, отображаемое в списке объектов.  
  
 Если COM-объект не реализует <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, **свойства** окне отображается имя интерфейса вместо имени объекта в левой части списка.  
  
## <a name="see-also"></a>См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)
