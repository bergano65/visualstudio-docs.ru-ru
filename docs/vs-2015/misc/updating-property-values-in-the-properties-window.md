---
title: Обновление значений свойств в окне «Свойства» | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 0272ba348e29fb1a2a118a0ff4b0989a2aa1683f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562052"
---
# <a name="updating-property-values-in-the-properties-window"></a>Обновление значений свойств в окне "Свойства"
Существует два способа поддерживать синхронизацию окна **Свойства** с изменениями значения свойства. Первый способ — вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс, который предоставляет доступ к базовой функциональности окон, включая доступ и Создание окон инструментов и документов, предоставляемую средой. Следующие шаги описывают этот процесс синхронизации.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Обновление значений свойств с помощью IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Обновление значений свойств с помощью интерфейса IVsUIShell  
  
1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (через <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> службы) каждый раз, когда пакетам VSPackage, проекты, или редакторам необходимо создать или перечислить окна инструментов или документов.  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> следует **свойства** синхронизацию с изменениями свойств для проекта окна (или любого другого выбранного объекта, который просматривается в **свойства** окно) без реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> и инициирования <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> события.  
  
3.  Реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> для установки и отключения, соответственно, уведомление клиента о событиях иерархии, не требуя от иерархии реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
## <a name="updating-property-values-using-iconnection"></a>Обновление значений свойств с помощью IConnection  
 Второй способ поддерживать синхронизацию окна **Свойства** с изменениями значений свойств — реализовать `IConnection` в доступном для подключения объекте, чтобы указать наличие исходящих интерфейсов. Если требуется локализовать имя свойства, создайте производный объект от <xref:System.ComponentModel.ICustomTypeDescriptor>. <xref:System.ComponentModel.ICustomTypeDescriptor> Реализации можно изменять возвращаемые дескрипторы свойств и измените имя свойства. Чтобы локализовать описание, создайте атрибут, который является производным от <xref:System.ComponentModel.DescriptionAttribute> и переопределите свойство Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Рекомендации по реализации интерфейса IConnection  
  
1.  `IConnection` предоставляет доступ к подобъекту перечислителя, с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> интерфейс. Он также предоставляет доступ для всех подобъектов точки соединения, каждый из которых реализует <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейс.  
  
2.  Любой объект обзора отвечает за реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> событий. Окно **Свойства** будет содержать рекомендацию события, заданного через `IConnection`.  
  
3.  Точка подключения определяет, сколько подключений (один или несколько), который позволяет, в своей реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Точка подключения, которая разрешает только один интерфейс может возвращать <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> из <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> метод.  
  
4.  Клиент может вызвать `IConnection` интерфейс для получения доступа к подобъекту перечислителя, с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> интерфейс. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Интерфейс можно затем вызвать для перечисления точек подключения для каждого исходящего идентификатора интерфейса (IID).  
  
5.  `IConnection` также можно вызывать для получения доступа к подобъектам точки подключения с <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейс для каждого исходящего IID. Через <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейс, клиент начинает или заканчивает рекомендательный цикл с помощью доступного для соединения объекта и собственной синхронизацией клиента. Клиент также может вызывать <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейс для получения объекта перечислителя с <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> интерфейс для перечисления сведений о соединениях.  
  
## <a name="see-also"></a>См. также  
 [Отслеживание выделения в окне свойств](../misc/announcing-property-window-selection-tracking.md)   
 [Расширение свойств](../extensibility/internals/extending-properties.md)