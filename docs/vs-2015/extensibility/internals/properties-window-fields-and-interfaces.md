---
title: Поля и интерфейсы окна свойств | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b58314d64536ecf33cc5589609ee5524a9352629
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700826"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Модель выбора позволяет определить, какие сведения отображаются в окне **Свойства** , на основе окна, имеющего фокус в интегрированной среде разработки. Для каждого окна и объекта в выбранном окне может быть отправлен объект контекста выбора в глобальный контекст выбора. Среда обновляет глобальный контекст выделения значениями из рамки окна, когда это окно находится в фокусе. При изменении фокуса, поэтому выполняет контекст выбора.  
  
## <a name="tracking-selection-in-the-ide"></a>Отслеживание выбора в интегрированной среде разработки  
 Для фрейма окна или сайта, принадлежащего интегрированной среде разработки, имеется служба с именем <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . В следующих шагах показано, как изменение в выделении, вызванное пользовательским изменением фокуса на другое открытое окно или выбором другого элемента проекта в **Обозреватель решений**, реализуется для изменения содержимого, отображаемого в окне « **свойства** ».  
  
1. Объект, созданный пакетом VSPackage, который набирается в выбранном окне, вызывает метод <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Контейнер выбора, предоставленный выбранным окном, создает собственный <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> объект. При изменении выбора пакет VSPackage вызывает <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> для уведомления всех прослушивателей в среде, включая окно **свойства** , для изменения. Он также предоставляет доступ к сведениям о иерархии и элементе, связанным с новым выбором.  
  
3. Вызов <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> и передача. выбранные элементы иерархии в `VSHPROPID_BrowseObject` параметре заполняют <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> объект.  
  
4. Для запрошенного элемента возвращается объект, производный от [интерфейса IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , и среда переносит его в <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (см. следующий шаг). Если вызов завершается неудачей, среда выполняет второй вызов `IVsHierarchy::GetProperty` , передавая ему контейнер выбора <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , предоставляемый элементом или элементами иерархии.  
  
    Проект VSPackage не создается <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , поскольку предоставляемый средой пакет VSPackage, реализующий его (например, **Обозреватель решений**) <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> от его имени.  
  
5. Среда вызывает методы <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> для получения объектов, основанных на `IDispatch` интерфейсе, для заполнения окна **свойств** .  
  
   При изменении значения в окне **свойств** пакеты VSPackage реализуют `IVsTrackSelectionEx::OnElementValueChangeEx` и `IVsTrackSelectionEx::OnSelectionChangeEx` сообщают об изменении значения элемента. Затем среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> или <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> , чтобы информация, отображаемая в окне **свойств** , была синхронизирована со значениями свойств. Дополнительные сведения см. [в разделе Обновление значений свойств в окне "Свойства"](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Помимо выбора другого элемента проекта в **Обозреватель решений** для вывода свойств, относящихся к этому элементу, можно также выбрать другой объект в форме или окне документа с помощью раскрывающегося списка, доступного в окне « **свойства** ». Дополнительные сведения см. в разделе [список объектов окна свойств](../../extensibility/internals/properties-window-object-list.md).  
  
   Можно изменить способ отображения сведений в сетке окна **свойств** в алфавитном порядке по категориям, а также, если это возможно, открыть страницу свойств для выбранного объекта, нажав соответствующие кнопки в окне « **свойства** ». Дополнительные сведения см. в разделе [кнопки окна свойств](../../extensibility/internals/properties-window-buttons.md) и [страницы свойств](../../extensibility/internals/property-pages.md).  
  
   Наконец, в нижней части окна **Свойства** также содержится описание поля, выбранного в сетке окна **свойства** . Дополнительные сведения см. [в разделе Получение описаний полей из окна "Свойства"](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>См. также:  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)
