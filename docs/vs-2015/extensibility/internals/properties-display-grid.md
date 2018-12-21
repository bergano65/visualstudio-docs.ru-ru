---
title: Свойства отображения сетки | Документация Майкрософт
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
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1a3db18bacb2aee7bd908be4246c1ce0701e8fee
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741386"
---
# <a name="properties-display-grid"></a>Отображение сетки свойств
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Свойства** окно отображает поля в сетке. Левый столбец содержит имена свойств; правый столбец содержит значения свойств.  
  
## <a name="working-with-the-grid"></a>Работа с сеткой  
 В списке два столбца отображаются свойства конфигурациями, которые могут быть изменены во время разработки и их текущих значений. Обратите внимание, что все свойства могут не отображаться. Свойство может быть задано как скрытый, например, путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> метод. В частности, чтобы скрыть свойства, имеющих дочерние свойства см. в разделе [скрытие свойств, имеют свойства дочерних элементов](../../misc/hiding-properties-that-have-child-properties.md).  
  
 Чтобы сведения об операциях отправки для **свойства** окна, интегрированная среда разработки использует <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> вызывается для каждого окна, содержащий выбираемых объектов с помощью связанных свойств для отображения в пакеты VSPackage **свойства** окна. **Обозреватель решений**в реализации <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> вызовы `GetProperty` с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> в иерархии проекта для получения доступные для просмотра объектов в иерархии.  
  
 Если VSPackage не поддерживает <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, IDE пытается использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> с использованием значения для <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , указать или несколько элементов иерархии.  
  
 Проект VSPackage не нужно создавать <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> так, как пакет предоставляемую интегрированной среды разработки окна, реализующий его (например, **обозревателе решений**) создает <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> от его имени.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> состоит из трех методов, которые вызываются с помощью IDE:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> содержит число объектов, выбранных для отображения в **свойства** окна.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Возвращает `IDispatch` объектов, выбранных для отображения в **свойства** окна.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> делает возможным для любого из объектов, возвращенных <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> выбираемые пользователем. Это позволяет VSPackage визуально обновить элементы, отображаемые для пользователя в пользовательском Интерфейсе.  
  
  **Свойства** окно извлекает сведения из `IDispatch` объектов для извлечения свойств, в который просматривается. В обозревателе свойств используются `IDispatch` попросить какие свойства объекта, он поддерживает, запросив `ITypeInfo`, которое было получено из `IDispatch::GetTypeInfo`. Затем браузер будет использовать эти значения для заполнения **свойства** окно и изменение значения отдельных свойств, отображаемых в сетке. Сведения о свойствах поддерживается внутри самого объекта.  
  
  Так как возвращаемые объекты поддерживают `IDispatch`, вызывающая сторона может получать сведения, такие как имя объекта, вызывая `IDispatch::Invoke` или `ITypeInfo::Invoke` с идентификатором предопределенные диспетчеризации (DISPID), который представляет нужные сведения. Объявленный DISPID имеет отрицательное значение, чтобы убедиться, что они не конфликтуют с определенные пользователем идентификаторы.  
  
  **Свойства** окне отображаются различные типы полей в зависимости от атрибутов свойств выбранного объекта. Эти поля включают поля ввода, раскрывающиеся списки и ссылки на диалоговые окна специализированного редактора.  
  
- Значения, содержащиеся в пронумерованном списке извлекаются путем <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> запрос, `IDispatch`. Значения, полученные из списка можно изменить в таблице свойств, дважды щелкнув имя поля или выбрав значение и выбрав новое значение из раскрывающегося списка. Для свойств, которые имеют предопределенные параметры из перечислимые списки дважды щелкнув имя свойства в списке свойств циклический перебор доступных вариантов. Для стандартных свойств только два варианта, такие как true или false дважды щелкните имя свойства для переключения между вариантами.  
  
- Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> является `false`, указывающее, что значение было изменено, значение отображается полужирным шрифтом. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> используется для определения того, если значение можно сбросить к исходному значению. Если таким образом, можно изменить значение по умолчанию, щелкнув его правой кнопкой мыши и выбрав **Сброс** из меню. В противном случае необходимо вручную изменить значение по умолчанию. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> также позволяет локализовать и скрыть имена свойств, отображаемых во время разработки, но не влияет на имена свойств, отображаемых во время выполнения.  
  
- Нажав кнопку с многоточием (...) список значений свойств, из которых пользователь может выбрать (например, палитра цветов или списка шрифтов). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> предоставляет эти значения.  
  
## <a name="see-also"></a>См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)

