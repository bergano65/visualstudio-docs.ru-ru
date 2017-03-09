---
title: "Обновление значений свойств в окне &quot;Свойства&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "окно свойств, обновление значений свойств"
  - "значения свойств, обновление в окне свойств"
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Обновление значений свойств в окне &quot;Свойства&quot;
Существует два способа поддерживать синхронизацию окна **Свойства** с изменениями значения свойства. Первый способ — вызывать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, который предоставляет доступ к базовым функциям окон, включая создание окон инструментов и документов, предоставляемых средой, и доступ к ним. Следующие шаги описывают этот процесс синхронизации.  
  
## Обновление значений свойств с помощью IVsUIShell  
  
#### Обновление значений свойств с помощью интерфейса IVsUIShell  
  
1.  Вызывайте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> \(через службу <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>\) каждый раз, когда пакетам VSPackage, проектам или редакторам необходимо создать или перечислить окна инструментов или документов.  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> для поддержания синхронизации окна **Свойства** с изменениями свойств для проекта \(или любого другого выбранного объекта, который просматривается в окне **Свойства**\) без реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> и инициирования событий <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A>.  
  
3.  Реализуйте методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> соответственно для установки и отключения уведомлений клиента о событиях иерархии, не требуя от иерархии реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
## Обновление значений свойств с помощью IConnection  
 Второй способ поддерживать синхронизацию окна **Свойства** с изменениями значений свойств — реализовать `IConnection` в доступном для подключения объекте, чтобы указать наличие исходящих интерфейсов. Если требуется локализовать имя свойства, создайте производный объект из <xref:System.ComponentModel.ICustomTypeDescriptor>. Реализация <xref:System.ComponentModel.ICustomTypeDescriptor> может изменять возвращаемые дескрипторы свойств и имя свойства. Чтобы локализовать описание, создайте атрибут, который является производным от <xref:System.ComponentModel.DescriptionAttribute>, и переопределите свойство Description.  
  
#### Рекомендации по реализации интерфейса IConnection  
  
1.  `IConnection` предоставляет доступ к подобъекту перечислителя с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Он также предоставляет доступ для всех подобъектов точки соединения, каждый из которых реализует интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.  
  
2.  Любой объект обзора отвечает за реализацию события <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. Окно **Свойства** будет содержать рекомендацию события, заданного через `IConnection`.  
  
3.  Точка подключения определяет, сколько подключений \(одно или несколько\) разрешено в его реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Точка подключения, которая разрешает только один интерфейс, может возвращать <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> из метода <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.  
  
4.  Клиент может вызвать интерфейс `IConnection` для получения доступа к подобъекту перечислителя с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> затем можно вызвать для перечисления точек подключения для каждого исходящего идентификатора интерфейса \(IID\).  
  
5.  `IConnection` также можно вызывать для получения доступа к подобъектам точки подключения с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> для каждого исходящего IID. Через интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> клиент запускает или завершает работу цикла рекомендаций с доступным для подключения объектом и собственной синхронизацией клиента. Клиент может также вызывать интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> для получения объекта перечислителя с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> для перечисления подключений, о которых ему известно.  
  
## См. также  
 [Отслеживание выделения в окне свойств](/visual-cpp/misc/announcing-property-window-selection-tracking)   
 [Расширение свойств](../extensibility/internals/extending-properties.md)