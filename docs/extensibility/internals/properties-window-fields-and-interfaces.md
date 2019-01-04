---
title: Свойства Window Fields and Interfaces | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98b5069a6b3709b467386a5424fded0809367a44
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872232"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
Модель для выбора определить, какие данные будут отображаться в **свойства** окна основана на окно, которое имеет фокус в интегрированной среде разработки. Каждой окна, а объект внутри выбранного окна, может иметь свой объект контекста выбора, в контексте глобального выделения. Среде обновляет контекст глобального выделения значениями из рамки окна, когда это окно имеет фокус. При изменении фокуса, заканчивается контекст выделения.  
  
## <a name="tracking-selection-in-the-ide"></a>Отслеживание выделения в интегрированной среде разработки  
 Рамка окна или сайта, принадлежащие интегрированной среды разработки, предоставляет службу <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Ниже показано, как изменение в выделенной области, из-за изменения фокуса на другое окно открытым или выбора элемента другого проекта в **обозревателе решений**, реализуется, чтобы изменить содержимое, отображаемое в  **Свойства** окна.  
  
1. Объект, созданный VSPackage, размещаемым в вызовах выбранное окно <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> иметь <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> вызова <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2. Контейнер выделения, предоставляемые выбранного окна, создает свой собственный <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> объекта. Когда изменения выделения, VSPackage вызывает <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> для уведомления все прослушиватели в среде, включая **свойства** окно изменения. Он также предоставляет доступ к иерархии и элемента сведения, связанные с новым выделением.  
  
3. Вызов <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> и передавая ему элементы выбранной иерархии в `VSHPROPID_BrowseObject` заполняет параметр <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> объекта.  
  
4. Объект, производный от [интерфейса IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) возвращается для <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> запрошенный элемент и среде помещает его в <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (см. следующий шаг). Если вызов завершается сбоем, среда предоставляет второй вызов `IVsHierarchy::GetProperty`, передав его в контейнере выделения <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , указать или несколько элементов иерархии.  
  
    Проект VSPackage не приводит к созданию <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> так, как окно предоставляемую среду пакет VSPackage, реализующий его (например, **обозревателе решений**) создает <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> от его имени.  
  
5. Среда вызывает методы <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> для получения объектов, на основе `IDispatch` интерфейсе заполнить **свойства** окна.  
  
   Если значение в **свойства** окна изменяется, пакеты VSPackage реализовывать `IVsTrackSelectionEx::OnElementValueChangeEx` и `IVsTrackSelectionEx::OnSelectionChangeEx` для занесения изменений в значение элемента. Затем среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> или <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> для сохранения информации, отображаемой в **свойства** окно синхронизированными со значениями свойства. Дополнительные сведения см. в разделе [обновление значений свойств в окне «Свойства»](#updating-property-values-in-the-properties-window).  
  
   Помимо выбора другого элемента проекта в **обозревателе решений** для отображения свойства, относящиеся к этому элементу, можно также выбрать другой объект из окна формы или документ, с помощью доступных на стрелку раскрывающегося списка **Свойства** окна. Дополнительные сведения см. в разделе [список объектов окна свойств](../../extensibility/internals/properties-window-object-list.md).  
  
   Вы можете изменить способ сведения отображаются в **свойства** таблица в окне в алфавитном порядке в категориальные, и, если он доступен, можно открыть страницу свойств для выбранного объекта с помощью соответствующих кнопок на  **Свойства** окна. Дополнительные сведения см. в разделе [кнопки окна свойств](../../extensibility/internals/properties-window-buttons.md) и [страницы свойств](../../extensibility/internals/property-pages.md).  
  
   Наконец, внизу **свойства** окно также содержит описание поля, выбранного в **свойства** окна сетки. Дополнительные сведения см. в разделе [Получение описаний полей из окна свойств](#getting-field-descriptions-from-the-properties-window).  
  
## <a name="updating-property-values-in-the-properties-window"></a> Обновление значений свойств в окне «Свойства»
Существует два способа поддерживать синхронизацию окна **Свойства** с изменениями значения свойства. Первый способ — вызывать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, который предоставляет доступ к базовым функциям окон, включая создание окон инструментов и документов, предоставляемых средой, и доступ к ним. Следующие шаги описывают этот процесс синхронизации.  
  
### <a name="updating-property-values-using-ivsuishell"></a>Обновление значений свойств с помощью IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Обновление значений свойств с помощью интерфейса IVsUIShell  
  
1.  Вызывайте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (через службу <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>) каждый раз, когда пакетам VSPackage, проектам или редакторам необходимо создать или перечислить окна инструментов или документов.  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> следует **свойства** синхронизацию с изменениями свойств для проекта окна (или любого другого выбранного объекта, который просматривается в **свойства** окно) без реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> и инициирования <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> события.  
  
3.  Реализуйте методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> соответственно для установки и отключения уведомлений клиента о событиях иерархии, не требуя от иерархии реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
### <a name="updating-property-values-using-iconnection"></a>Обновление значений свойств с помощью IConnection  
 Второй способ поддерживать синхронизацию окна **Свойства** с изменениями значений свойств — реализовать `IConnection` в доступном для подключения объекте, чтобы указать наличие исходящих интерфейсов. Если требуется локализовать имя свойства, создайте производный объект из <xref:System.ComponentModel.ICustomTypeDescriptor>. Реализация <xref:System.ComponentModel.ICustomTypeDescriptor> может изменять возвращаемые дескрипторы свойств и имя свойства. Чтобы локализовать описание, создайте атрибут, который является производным от <xref:System.ComponentModel.DescriptionAttribute>, и переопределите свойство Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Рекомендации по реализации интерфейса IConnection  
  
1.  `IConnection` предоставляет доступ к подобъекту перечислителя с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Он также предоставляет доступ для всех подобъектов точки соединения, каждый из которых реализует интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.  
  
2.  Любой объект обзора отвечает за реализацию события <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. Окно **Свойства** будет содержать рекомендацию события, заданного через `IConnection`.  
  
3.  Точка подключения определяет, сколько подключений (одно или несколько) разрешено в его реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Точка подключения, которая разрешает только один интерфейс, может возвращать <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> из метода <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.  
  
4.  Клиент может вызвать интерфейс `IConnection` для получения доступа к подобъекту перечислителя с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> затем можно вызвать для перечисления точек подключения для каждого исходящего идентификатора интерфейса (IID).  
  
5.  `IConnection` также можно вызывать для получения доступа к подобъектам точки подключения с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> для каждого исходящего IID. Через интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> клиент запускает или завершает работу цикла рекомендаций с доступным для подключения объектом и собственной синхронизацией клиента. Клиент может также вызывать интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> для получения объекта перечислителя с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> для перечисления подключений, о которых ему известно.  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a> Получение описаний полей из окна свойств
В нижней части окна **Свойства** в области описания отображаются сведения, относящиеся к выбранному полю свойства. Эта функция включена по умолчанию. Если необходимо скрыть поле описания, правой кнопкой мыши щелкните окно **Свойства** и выберите пункт **Описание**. При этом также снимается флажок рядом с заголовком **Описание** в окне меню. Чтобы отобразить поле повторно, выполните те же действия для включения пункта **Описание** .  
  
 Сведения в поле "Описание" поступают из <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Каждый метод, интерфейс, компонентный класс и т. д. может иметь нелокализованный атрибут `helpstring` в библиотеке типов. **Свойства** окно получает строку из <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Указание локализованных строк справки  
  
1. Добавьте атрибут `helpstringdll` в инструкцию библиотеки в библиотеке типов (`typelib`).  
  
   > [!NOTE]
   >  Этот шаг является необязательным, если библиотека типов находится в файле библиотеки (OLB-файле).  
  
2. Укажите атрибуты `helpstringcontext` для строк. Можно также указать атрибуты `helpstring` .  
  
    Они отличаются от атрибутов `helpfile` и `helpcontext` , которые содержатся в реальных разделах справки в формате CHM.  
  
   Чтобы получить описание, которое будет отображаться для выбранного имени свойства, **свойства** вызовы в окна <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> для выбранного свойства с указанием нужного `lcid` для атрибута Выходная строка. На внутреннем уровне <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> находит DLL-файл, указанный в атрибуте `helpstringdll`, и вызывает в этом файле метод `DLLGetDocumentation` с заданным контекстом и атрибутом `lcid`.  
  
   Подпись и реализация метода `DLLGetDocumentation` выглядят следующим образом.  
  
```cpp  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 Функция `DLLGetDocumentation` должна быть функцией экспорта, определенной в DEF-файле библиотеки DLL.  
  
 На внутреннем уровне создается OLB-файл, который на самом деле является библиотекой DLL. Эта библиотека DLL содержит один ресурс — файл библиотеки типов (TLB-файл) — и одну экспортированную функцию — `DLLGetDocumentation`.  
  
 Что касается OLB-файлов, атрибут `helpstringdll` является необязательным, так как это тот же файл, содержащий сам TLB-файл.  
  
 Таким образом, чтобы строки отображались в области **Описание** , нужно по меньшей мере указать атрибут `helpstring` в библиотеке типов. Если эти строки требуется локализовать, необходимо указать необязательный атрибут `helpstringdll` и обязательный атрибут `helpstringcontext` , а затем реализовать `DLLGetDocumentation`.  
  
 При получении локализованных сведений с помощью атрибута `helpstringcontext` idl и `DLLGetDocumentation` реализовывать дополнительные интерфейсы не нужно.  
  
 Другим способом получения локализованного имени и описания свойства является реализация метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Дополнительные сведения, относящиеся к реализации этого метода, см. в статье [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md).  

## <a name="see-also"></a>См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)