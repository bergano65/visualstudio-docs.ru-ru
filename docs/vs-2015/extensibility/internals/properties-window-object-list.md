---
title: Список объектов окна свойств | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87592deaec57b5638336cf191f12896cccbcb5b3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572475"
---
# <a name="properties-window-object-list"></a>Список объектов окна свойств
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [список объектов окна свойств](https://docs.microsoft.com/visualstudio/extensibility/internals/properties-window-object-list).  
  
Список объектов в **свойства** окно является список раскрывающегося списка, который позволяет изменить выделение на другие объекты, доступные в один или несколько выбранных периодов. Выбрав другой объект из этого списка запускает вызов <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> сообщать среде, что был выбран новый объект. Информация, отображаемая в **свойства** окно затем изменяется для отображения свойства, связанные с вновь выбранный объект.  
  
## <a name="the-object-list"></a>Список объектов  
 Список объектов состоит из двух полей: имя объекта (отображается полужирным шрифтом) и тип объекта.  
  
 Имя объекта, который отображается слева от типа объекта полужирным шрифтом, извлекается из самого объекта с помощью `Name` свойства, предоставляемые <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> интерфейс. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, единственный метод на <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, возвращает <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> для компонентного класса этот интерфейс. **Свойства** использует окно <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> получить имя компонентного класса, которое отображается как имя объекта в раскрывающемся списке.  
  
 Если объект не имеет `Name` свойство, имя не отображается в области имя списка объектов. Свойство Name можно добавить к объекту, если вы хотите, чтобы имя, отображаемое в списке объектов.  
  
 Если COM-объект не реализует <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, **свойства** окне отображается имя интерфейса вместо имени объекта в левой части списка.  
  
## <a name="see-also"></a>См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)

