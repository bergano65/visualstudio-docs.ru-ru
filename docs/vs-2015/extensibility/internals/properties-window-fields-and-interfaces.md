---
title: Свойства Window Fields and Interfaces | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3aa3daa8925c9fec79f80d4d2fa6b4e8365b15b2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929339"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Модель для выбора определить, какие данные будут отображаться в **свойства** окна основана на окно, которое имеет фокус в интегрированной среде разработки. Каждой окна, а объект внутри выбранного окна, может иметь свой объект контекста выбора, в контексте глобального выделения. Среде обновляет контекст глобального выделения значениями из рамки окна, когда это окно имеет фокус. При изменении фокуса, заканчивается контекст выделения.  
  
## <a name="tracking-selection-in-the-ide"></a>Отслеживание выделения в интегрированной среде разработки  
 Рамка окна или сайта, принадлежащие интегрированной среды разработки, предоставляет службу <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Ниже показано, как изменение в выделенной области, из-за изменения фокуса на другое окно открытым или выбора элемента другого проекта в **обозревателе решений**, реализуется, чтобы изменить содержимое, отображаемое в  **Свойства** окна.  
  
1. Объект, созданный VSPackage, размещаемым в вызовах выбранное окно <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> иметь <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> вызова <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2. Контейнер выделения, предоставляемые выбранного окна, создает свой собственный <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> объекта. Когда изменения выделения, VSPackage вызывает <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> для уведомления все прослушиватели в среде, включая **свойства** окно изменения. Он также предоставляет доступ к иерархии и элемента сведения, связанные с новым выделением.  
  
3. Вызов <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> и передавая ему элементы выбранной иерархии в `VSHPROPID_BrowseObject` заполняет параметр <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> объекта.  
  
4. Объект, производный от [интерфейса IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) возвращается для <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> запрошенный элемент и среде помещает его в <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (см. следующий шаг). Если вызов завершается сбоем, среда предоставляет второй вызов `IVsHierarchy::GetProperty`, передав его в контейнере выделения <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , указать или несколько элементов иерархии.  
  
    Проект VSPackage не приводит к созданию <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> так, как окно предоставляемую среду пакет VSPackage, реализующий его (например, **обозревателе решений**) создает <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> от его имени.  
  
5. Среда вызывает методы <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> для получения объектов, на основе `IDispatch` интерфейсе заполнить **свойства** окна.  
  
   Если значение в **свойства** окна изменяется, пакеты VSPackage реализовывать `IVsTrackSelectionEx::OnElementValueChangeEx` и `IVsTrackSelectionEx::OnSelectionChangeEx` для занесения изменений в значение элемента. Затем среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> или <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> для сохранения информации, отображаемой в **свойства** окно синхронизированными со значениями свойства. Дополнительные сведения см. в разделе [обновление значений свойств в окне «Свойства»](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Помимо выбора другого элемента проекта в **обозревателе решений** для отображения свойства, относящиеся к этому элементу, можно также выбрать другой объект из окна формы или документ, с помощью доступных на стрелку раскрывающегося списка **Свойства** окна. Дополнительные сведения см. в разделе [список объектов окна свойств](../../extensibility/internals/properties-window-object-list.md).  
  
   Вы можете изменить способ сведения отображаются в **свойства** таблица в окне в алфавитном порядке в категориальные, и, если он доступен, можно открыть страницу свойств для выбранного объекта с помощью соответствующих кнопок на  **Свойства** окна. Дополнительные сведения см. в разделе [кнопки окна свойств](../../extensibility/internals/properties-window-buttons.md) и [страницы свойств](../../extensibility/internals/property-pages.md).  
  
   Наконец, внизу **свойства** окно также содержит описание поля, выбранного в **свойства** окна сетки. Дополнительные сведения см. в разделе [Получение описаний полей из окна свойств](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)

