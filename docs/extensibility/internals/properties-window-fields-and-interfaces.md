---
title: "Поля окна свойств и интерфейсы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Окно свойств, полей и интерфейсы"
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Поля окна свойств и интерфейсы
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Модель для выделения, чтобы указать, какие сведения представлены в **Свойства** окно основано на поле, имеющее фокус в интегрированной среде разработки.  Каждое поле и объект внутри выбранного окна, могут быть отправлянный контекстный объект выделения к глобальным контекстом выделения.  Среда обновляет контекст выделения значениями из глобальных границы окна, если окно находится в фокусе.  При изменении фокуса, так выполняет контекст выделения.  
  
## Выделение отслеживания в интегрированной среде разработки  
 Граница окна или сайт, принадлежащих интегрированной средой разработки, называемую службы имеют <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>.  Следующие шаги показывают, как изменения в выделении, причиненном пользователем, то при изменении фокуса другому открыть окно или другой элемент проекта в выделение **Обозреватель решений**реализует, чтобы изменить содержимое, отображаемое в  **Свойства** окна.  
  
1.  Объект, созданный в VSPackage, располагается в выбранных вызовы окна <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> having  <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> вызовите  <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Контейнер выделения, при условии, что выбранным окном, создает свои <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> объект.  При изменении выделения, вызовы VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> уведомить всех прослушивателей в такой среде, включая  **Свойства** окно, изменения.  Он также предоставляет доступ к данным по иерархии и элементов, связанным с новое выделение.  
  
3.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> и передавая ему выбранные элементы в иерархии  `VSHPROPID_BrowseObject` параметр заполняет  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> объект.  
  
4.  Объект, производный от [интерфейс IDispatch](http://msdn.microsoft.com/ru-ru/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) возвращает для  <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> для запрошенного элемента и создает ее в программу\-оболочку среды  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> \(см. следующий этап\).  Если вызов завершается ошибкой, то среда совершает второй к `IVsHierarchy::GetProperty`контейнер выделения, передавая ему  <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> почту, что элемент иерархии или элементов.  
  
     Проект не создает VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> поскольку среда\-поставленное окно VSPackage, реализующий его конфигурации \(например,  **Обозреватель решений**конструкции\)  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> от его имени.  
  
5.  Среда вызывает методы <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> получить объекты на основании  `IDispatch` интерфейс для заполнения  **Свойства** окна.  
  
 Если значение **Свойства** изменено окне инструмент VSPackages  `IVsTrackSelectionEx::OnElementValueChangeEx` и  `IVsTrackSelectionEx::OnSelectionChangeEx` изменение отчета в значение элемента.  Среда затем вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> OR  <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> хранить данные выводятся в  **Свойства** окно синхронизированное со значениями свойств.  Дополнительные сведения см. в разделе [Обновление значений свойств в окне "Свойства"](../../misc/updating-property-values-in-the-properties-window.md).  
  
 Помимо выбора другого элемента в проект **Обозреватель решений** для отображения свойств, относящихся к данному элементу можно также выбрать другой объект из формы или окна документа с помощью раскрывающегося списка доступных  **Свойства** окна.  Дополнительные сведения см. в разделе [Список объектов окна свойств](../../extensibility/internals/properties-window-object-list.md).  
  
 Можно изменить способ данные выводятся в **Свойства** сетка окна из алфавитного к категорически и, если это возможно, можно также открыть страницу свойств выбранного объекта, нажимая соответствующие кнопки  **Свойства** окна.  Дополнительные сведения см. в разделах [Кнопки окна свойств](../../extensibility/internals/properties-window-buttons.md) и [Страницы свойств](../../extensibility/internals/property-pages.md).  
  
 Наконец, bottom **Свойства** окно также содержит описание выбранного поля  **Свойства** сетка окна.  Дополнительные сведения см. в разделе [Получение описаний полей из окна "Свойства"](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)