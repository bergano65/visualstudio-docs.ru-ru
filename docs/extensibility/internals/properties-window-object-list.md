---
title: Список объектов окна свойств (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffe11ae6ebb4e692686c884b663a4f93d1466535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706149"
---
# <a name="properties-window-object-list"></a>Список объектов окна свойств
Список объектов в окне **Свойств** представляет собой список выпадающих, который позволяет изменять выбор на другие объекты, доступные в одном или нескольких выбранных окнах. Выбор другого объекта из этого списка вызывает <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> вызов для информирования среды о том, что выбран новый объект. Затем информация, отображаемый в окне **Свойств,** изменяется, чтобы показать свойства, связанные с недавно выбранным объектом.

## <a name="the-object-list"></a>Список объектов
 Список объектов состоит из двух полей: имени объекта (отображается жирным шрифтом) и типа объекта.

 Имя объекта, отображаемое слева от типа объекта жирным `Name` шрифтом, <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> извлекается из самого объекта с помощью свойства, предоставляемого интерфейсом. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, единственный <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>метод <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> на , возвращается для совместного класса этого интерфейса. Окно **Свойства** <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> использует для получения имени coclass, которое отображается как имя объекта в списке выпадающих.

 Если объект не имеет `Name` свойства, имя не отображается в области имени списка объектов. Вы можете добавить свойство «Имя» объекту, если требуется, чтобы имя было отображено в списке объектов.

 Если объект COM не <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>выполняется, окно **Свойств** отображает имя интерфейса вместо имени объекта в левой части списка.

## <a name="see-also"></a>См. также
- [Расширение свойств](../../extensibility/internals/extending-properties.md)
