---
title: "Отображение сетки свойств | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Свойства сетки [Visual Studio SDK]"
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Отображение сетки свойств
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**Свойства** отображает поля окна в сетке.  В левом столбце содержатся имена свойств; правый столбец содержит значения свойства.  
  
## Работа с сеткой  
 2 Конфигурация\-независимые на список столбцов содержит свойства, которые можно изменить во время разработки и их текущих параметрах.  Обратите внимание, что все свойства могут не отображаться.  Свойство может быть задано как скрыть, например с помощью реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> метод.  В частности, скрывать свойства, имеющие свойства дочерних элементов увидеть [Скрытие свойств, имеющих дочерние свойства](../../misc/hiding-properties-that-have-child-properties.md).  
  
 Отправить данные в **Свойства** окно, интегрированная среда разработки использует  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> вызывает VSPackages для каждого окна, которое содержит отдельные объекты, связанные свойства, отображаемое в  **Свойства** окна.  **Обозреватель решений**'реализация s   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> вызовы  `GetProperty` использование  <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> в иерархии проекта для получения browseable объектов в иерархии.  
  
 Если в VSPackage не поддерживается <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>интегрированная среда разработки пытается использовать  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> использование значение  <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> почту, что элемент иерархии или элементов.  
  
 Не следует создать проект VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> поскольку среда разработки\-поставленный пакет окна, реализующий его конфигурации \(например,  **Обозреватель решений**конструкции\)  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> от его имени.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> состоит из 3 методов, которые вызываются средой разработки:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> содержит число объектов, выбранных отображаться в  **Свойства** окна.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> возвращает  `IDispatch` объекты, выбранные отображаться в  **Свойства** окна.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> делает возможным для всех возвращаемых объектов by  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> быть выбран пользователем.  Это позволяет визуально VSPackage для обновления выделение отображаются пользователю в пользовательском интерфейсе.  
  
 **Свойства** извлекает сведения из окна  `IDispatch` объекты для извлечения, просмотретьыми свойства.  Обозреватель свойств использует `IDispatch` запросить объект свойства, он поддерживает путем запроса  `ITypeInfo`, из которого возвращает  `IDispatch::GetTypeInfo`.  Браузер затем использовать эти значения для заполнения **Свойства** окно, и изменяет значения для отдельных собственностей, отображаемых в сетке.  Данные свойств поддерживаются в сам объект.  
  
 Поскольку возвращаемая поддержка объектов `IDispatch`вызывающий код может получить такие сведения, как имя объекта, вызвав то  `IDispatch::Invoke` OR  `ITypeInfo::Invoke` с предопределенным идентификатором диспетчера \(DISPID\), представляющий желаемое сведения.  Объявленное идентификаторов dispid отрицательное, чтобы убедиться, что они не конфликтует с определяемыми пользователем идентификаторами.  
  
 **Свойства** окно показывает различные типы полей в зависимости от атрибутов, определенных свойств выбранного объекта.  Эти поля содержат поля ввода раскрывающемся списке и ссылки на диалоговые окна специализированного редактора.  
  
-   Значения, содержащиеся в пронумерованном списке получены a <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> запрос  `IDispatch`.  Значения, полученные из пронумерованного списка можно изменить в сетке свойств, дважды щелкните имя поля, щелкните значение и выбрать новое значение из раскрывающегося списка.  Для свойств, которые имеют предопределенные параметры из нумерованных списков, дважды щелкнув имя свойства в циклах списка свойств по доступным варианты.  Для стандартных свойств только с 2 вариантами выбора, такие как true и false, дважды щелкните имя свойства для переключения между вариантами выбора.  
  
-   If <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> существует  `false`, указывающее, что значение было изменено, значение отображается полужирным шрифтом.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> используется, чтобы определить, является ли значение можно сбросить к исходному значению.  Если да, можно изменить вернуться к значению по умолчанию, щелкнув правой кнопкой мыши и выбрать значение **Сброс** из отображенного меню.  В противном случае необходимо изменить значение вернуться к значению по умолчанию вручную.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> также можно локализовать и скрыть имена свойств, отображаемых во время разработки, но не влияет на имена свойств, отображаемых во время выполнения.  
  
-   Нажав кнопку с многоточием \(...\) указывает список значений свойств из которых пользователь может выбирать \(в виде списка цветов шрифта\) либо.  <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> предоставляет эти значения.  
  
## См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)