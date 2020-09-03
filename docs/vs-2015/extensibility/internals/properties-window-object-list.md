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
ms.openlocfilehash: 95ef509491e05daf575e211ae479c815994eb3d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148330"
---
# <a name="properties-window-object-list"></a>Список объектов окна свойств
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Список объектов в окне « **Свойства** » — это раскрывающийся список, позволяющий изменить выделенный фрагмент на другие объекты, доступные в одном или нескольких выбранных окнах. Выбор другого объекта из этого списка вызывает метод, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> чтобы сообщить среде о том, что был выбран новый объект. Сведения, отображаемые в окне **Свойства** , изменяются для отображения свойств, связанных с вновь выбранным объектом.  
  
## <a name="the-object-list"></a>Список объектов  
 Список объектов состоит из двух полей: имени объекта (отображается полужирным шрифтом) и типа объекта.  
  
 Имя объекта, отображаемое слева от типа объекта полужирным шрифтом, извлекается из самого объекта с помощью `Name` свойства, предоставленного <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> интерфейсом. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, единственный метод в <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , возвращает <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> для компонентного класса этого интерфейса. В окне **Свойства** используется <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> для получения имени компонентного класса, который отображается как имя объекта в раскрывающемся списке.  
  
 Если объект не имеет `Name` свойства, имя не отображается в области имен в списке объектов. Если требуется, чтобы имя отображалось в списке объектов, можно добавить в объект свойство Name.  
  
 Если COM-объект не реализует <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , в окне **свойства** отображается имя интерфейса вместо имени объекта в левой части списка.  
  
## <a name="see-also"></a>См. также:  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)
