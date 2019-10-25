---
title: Список объектов окна свойств | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e50b3fe46edb8d14cad9a03a45bc8650cb9713ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725190"
---
# <a name="properties-window-object-list"></a>Список объектов окна свойств
Список объектов в окне « **Свойства** » — это раскрывающийся список, позволяющий изменить выделенный фрагмент на другие объекты, доступные в одном или нескольких выбранных окнах. Выбор другого объекта в этом списке вызывает <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>, чтобы сообщить среде о том, что был выбран новый объект. Сведения, отображаемые в окне **Свойства** , изменяются для отображения свойств, связанных с вновь выбранным объектом.

## <a name="the-object-list"></a>Список объектов
 Список объектов состоит из двух полей: имени объекта (отображается полужирным шрифтом) и типа объекта.

 Имя объекта, отображаемое слева от типа объекта полужирным шрифтом, извлекается из самого объекта с помощью свойства `Name`, предоставляемого интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, единственный метод в <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, возвращает <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> для этого интерфейса. В окне " **Свойства** " используется <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> для получения имени компонентного класса, который отображается как имя объекта в раскрывающемся списке.

 Если объект не имеет свойства `Name`, имя не отображается в области имен списка объектов. Если требуется, чтобы имя отображалось в списке объектов, можно добавить в объект свойство Name.

 Если объект COM не реализует <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, в окне **Свойства** отображается имя интерфейса вместо имени объекта в левой части списка.

## <a name="see-also"></a>См. также
- [Расширение свойств](../../extensibility/internals/extending-properties.md)