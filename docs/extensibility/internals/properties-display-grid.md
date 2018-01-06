---
title: "Свойства отображения сетки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 88720010c178fb1ca3a4c2425002f5f34e26e777
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="properties-display-grid"></a>Отображение сетки свойств
**Свойства** окне будут отображаться поля элемента управления Grid. Левый столбец содержит имена свойств. правый столбец содержит значения свойств.  
  
## <a name="working-with-the-grid"></a>Работа с сеткой  
 В списке два столбца отображаются свойства зависят от конфигурации, которые могут быть изменены во время разработки и их текущих параметров. Обратите внимание, что все свойства могут не отображаться. Свойство может быть задано как скрытый, например, путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> метод. В частности, чтобы скрыть свойства, имеющие дочерние свойства:  
  
1.  Задать `pfDisplay` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> для `FALSE`.  
  
2.  Задать `pfHide` параметр в <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> для `TRUE`.  
  
 Для принудительной сведений **свойства** окне IDE использует <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>вызывается для каждого окна, который содержит доступный для выбора объектов, содержащих связанные свойства для отображения в пакеты VSPackage **свойства** окна. **Обозреватель решений**реализация <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> вызовы `GetProperty` с помощью <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> в иерархии проекта, чтобы получить доступные для просмотра объектов в иерархии.  
  
 Если VSPackage не поддерживает <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, IDE пытается использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> с использованием значения для <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , укажите иерархии или несколько элементов.  
  
 VSPackage необходимо создать проект <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> поскольку окна, предоставляемый интегрированной среды разработки пакета, реализует (например, **обозревателе решений**) создает <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> от его имени.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>состоит из трех методов, которые вызываются из интегрированной среды разработки.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>содержит число объектов, выбранных для отображения в **свойства** окна.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>Возвращает `IDispatch` объекты, выбранные для отображения в **свойства** окна.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>делает возможным для любых объектов, возвращенных <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> для выбранного пользователем. Это позволяет VSPackage визуально обновить элементы, отображаемые для пользователя в пользовательском Интерфейсе.  
  
 **Свойства** окна извлекает сведения из `IDispatch` объектов для получения свойств, в который просматривается. Свойства браузер использует `IDispatch` попросить какие свойства объекта, он поддерживает, запрашивая `ITypeInfo`, который получается из `IDispatch::GetTypeInfo`. Браузер, затем использует эти значения для заполнения **свойства** окна и изменение значения отдельных свойств отображаются в сетке. Данные свойства хранятся в сам объект.  
  
 Так как возвращаемые объекты поддерживают `IDispatch`, вызывающего объекта можно получить сведения, например имя объекта с помощью вызова `IDispatch::Invoke` или `ITypeInfo::Invoke` с идентификатором предопределенных диспетчеризации (DISPID), который представляет требуемую информацию. Чтобы убедиться, что они не конфликтовали с определенные пользователем идентификаторы отрицательны объявленный DISPID.  
  
 **Свойства** окне отображаются различные типы полей, в зависимости от атрибутов свойств выбранного объекта. Вот эти поля, поля ввода, раскрывающиеся списки и ссылки на диалоговые специализированный редактор.  
  
-   Значения, содержащиеся в пронумерованном списке извлекаются путем <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> запрос, `IDispatch`. Значения, полученные из нумерованный список можно изменить в таблице свойств, дважды щелкнув имя поля или щелкнуть значение и выбрать новое значение из раскрывающегося списка. Для свойств, которые имеют предопределенные параметры из перечисляемого списков дважды щелкните имя свойства в список свойств циклически доступны следующие возможности. Для стандартных свойств с только два варианта, такие как true или false дважды щелкните имя свойства для переключения между вариантами.  
  
-   Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> — `false`, указывающее, что значение было изменено, значение отображается полужирным шрифтом. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>используется для определения, если значение можно сбросить в исходное значение. Если таким образом, вы можете изменить значение по умолчанию, щелкнув значение правой кнопкой мыши и выбрав **Сброс** из меню. В противном случае необходимо вручную изменить значение по умолчанию. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>также дает возможность локализации и скрытие имен свойств, отображаемых во время разработки, но не влияет на имена свойств, отображаемых во время выполнения.  
  
-   Нажмите кнопку с многоточием (...) список значений свойств, из которых пользователь может выбрать (например, палитра цветов или списка шрифтов). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>предоставляет эти значения.  
  
## <a name="see-also"></a>См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)