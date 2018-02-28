---
title: "Поля окна свойств и интерфейсы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1f238cceb189723e3ec10fbf8db4abbd9675ae21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
Модель для выделения, чтобы определить, какие данные будут отображаться в **свойства** окно основано на окно, которое имеет фокус в Интегрированной среде разработки. Все окна и объекта в выбранный период, могут иметь его Выбор объекта контекста, помещаются в контекст глобального выделения. Среды обновляет контекст глобального выделения значениями из рамки окна, если это окно находится в фокусе. При изменении фокуса, поэтому не контекст выделения.  
  
## <a name="tracking-selection-in-the-ide"></a>Отслеживание выделения в Интегрированной среде разработки  
 Фрейм окна или на узле, принадлежащих IDE, имеет службу под названием <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Следующие шаги показывают, как изменения в выделенном фрагменте, вызванные пользователя изменения фокуса в другое окно открытым или выбора элемента в другом проекте **обозревателе решений**, реализуется, чтобы изменить содержимое, отображаемое в  **Свойства** окна.  
  
1.  Объект, созданный VSPackage, размещаемым в вызовах выбранное окно <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> иметь <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> вызова <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Контейнер выбора, предоставляемые выбранное окно создает собственный <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> объекта. При изменении выбора VSPackage вызывает <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> известить все прослушиватели в среде, включая **свойства** окно изменения. Он также предоставляет доступ к иерархии и элемента сведения, относящиеся к новое выделение.  
  
3.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> и передачи его элементы выбранной иерархии в `VSHPROPID_BrowseObject` заполняет параметр <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> объекта.  
  
4.  Объект, производный от [интерфейса IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) возвращается для <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> для запрошенного элемента и среде помещает его в <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (см. следующий шаг). При сбое вызова, среде выполняется второй вызов `IVsHierarchy::GetProperty`, передавая ему контейнера выделения <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , укажите иерархии или несколько элементов.  
  
     Проект VSPackage не приводит к созданию <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> так, как окно среды предоставленный VSPackage, реализующий его (например, **обозревателе решений**) создает <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> от его имени.  
  
5.  Среда вызывает методы <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> для получения объектов, на основе `IDispatch` интерфейс для заполнения **свойства** окна.  
  
 Если значение в **свойства** окна изменяется, пакеты VSPackage реализовывать `IVsTrackSelectionEx::OnElementValueChangeEx` и `IVsTrackSelectionEx::OnSelectionChangeEx` сообщить изменения значения элемента. Затем среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> или <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> для хранения сведений, отображаемых в **свойства** окна синхронизированы со значениями свойств. Дополнительные сведения см. в разделе [обновление значений свойств в окне «Свойства»](#updating-property-values-in-the-properties-window).  
  
 Помимо выбора другого элемента проекта в **обозревателе решений** для отображения свойства, относящиеся к этому элементу, можно также выбрать другой объект из формы или в окне документа с помощью доступны в раскрывающемся списке **Свойства** окна. Дополнительные сведения см. в разделе [списка объектов в окне свойств](../../extensibility/internals/properties-window-object-list.md).  
  
 Можно изменить способ отображения информации в **свойства** таблица в окне в алфавитном порядке для категориальных, и, если он доступен, можно открыть страницу свойств для выбранного объекта, нажимая соответствующие кнопки на  **Свойства** окна. Дополнительные сведения см. в разделе [кнопки окна свойств](../../extensibility/internals/properties-window-buttons.md) и [страницы свойств](../../extensibility/internals/property-pages.md).  
  
 Наконец, в нижней части **свойства** окно также содержит описание полей, выбранных в **свойства** окна сетки. Дополнительные сведения см. в разделе [Получение описаний полей из окна свойств](#getting-field-descriptions-from-the-properties-window).  
  
## <a name="updating-property-values-in-the-properties-window"></a>Обновление значений свойств в окне «Свойства»
Существует два способа поддерживать синхронизацию окна **Свойства** с изменениями значения свойства. Первый — вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> интерфейс, который предоставляет доступ к базовым функциям окон, включая доступ и создание окна инструментов и документов, предоставляемых средой. Следующие шаги описывают этот процесс синхронизации.  
  
### <a name="updating-property-values-using-ivsuishell"></a>Обновление значений свойств с помощью IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Обновление значений свойств с помощью интерфейса IVsUIShell  
  
1.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (через <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> службы) каждый раз, когда пакетам VSPackage, проектов или редакторам необходимо создать или перечислить окна инструментов или документов.  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> для сохранения **свойства** синхронизацию с изменениями свойств для проекта окна (или любого другого выбранного объекта, который просматривается в **свойства** окна) без реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> и инициирования <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> события.  
  
3.  Реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> для установки и отключения, соответственно, уведомление клиента событиях иерархии, не требуя от иерархии реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
### <a name="updating-property-values-using-iconnection"></a>Обновление значений свойств с помощью IConnection  
 Второй способ поддерживать синхронизацию окна **Свойства** с изменениями значений свойств — реализовать `IConnection` в доступном для подключения объекте, чтобы указать наличие исходящих интерфейсов. Если требуется локализовать имя свойства, создайте производный объект от <xref:System.ComponentModel.ICustomTypeDescriptor>. <xref:System.ComponentModel.ICustomTypeDescriptor> Реализации можно изменять возвращаемые дескрипторы свойств и измените имя свойства. Чтобы локализовать описание, создайте атрибут, который является производным от <xref:System.ComponentModel.DescriptionAttribute> и переопределите свойство Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Рекомендации по реализации интерфейса IConnection  
  
1.  `IConnection`предоставляет доступ к подобъекту перечислителя, с <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> интерфейса. Он также предоставляет доступ для всех подобъектов точки соединения, каждый из которых реализует <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейса.  
  
2.  Любой объект обзора отвечает за реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> событий. Окно **Свойства** будет содержать рекомендацию события, заданного через `IConnection`.  
  
3.  Точка подключения определяет, сколько подключений (одно или несколько) разрешено в своей реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Точка подключения, которая разрешает только один интерфейс может возвращать <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> из <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> метод.  
  
4.  Клиент может вызвать `IConnection` интерфейс для получения доступа к подобъекту перечислителя, с <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> интерфейса. <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Интерфейс может затем вызвать для перечисления точек подключения для каждого исходящего идентификатора интерфейса (IID).  
  
5.  `IConnection`также можно вызывать для получения доступа к подобъектам точки с <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейс для каждого исходящего IID. Через <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейса, клиент запускает или завершает работу цикла рекомендаций с доступным для подключения объектом и собственной синхронизацией клиента. Клиент может также вызывать <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейс для получения объекта перечислителя с <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> интерфейс для перечисления соединений, для которых ему известно.  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a>Получение описаний полей из окна «Свойства»
В нижней части окна **Свойства** в области описания отображаются сведения, относящиеся к выбранному полю свойства. Эта функция включена по умолчанию. Если необходимо скрыть поле описания, правой кнопкой мыши щелкните окно **Свойства** и выберите пункт **Описание**. При этом также снимается флажок рядом с заголовком **Описание** в окне меню. Чтобы отобразить поле повторно, выполните те же действия для включения пункта **Описание** .  
  
 В поле описания информацию можно получить из <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Каждый метод, интерфейс, компонентный класс и т. д. может иметь нелокализованный атрибут `helpstring` в библиотеке типов. **Свойства** получает строку из <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Указание локализованных строк справки  
  
1.  Добавьте атрибут `helpstringdll` в инструкцию библиотеки в библиотеке типов (`typelib`).  
  
    > [!NOTE]
    >  Этот шаг является необязательным, если библиотека типов находится в файле библиотеки (OLB-файле).  
  
2.  Укажите атрибуты `helpstringcontext` для строк. Можно также указать атрибуты `helpstring` .  
  
     Они отличаются от атрибутов `helpfile` и `helpcontext` , которые содержатся в реальных разделах справки в формате CHM.  
  
 Чтобы получить описание, которое будет отображаться для выбранного имени свойства, **свойства** вызывает <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> для выбранного свойства с указанием нужного `lcid` для атрибута Выходная строка. На внутреннем уровне <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> находит DLL-файл, указанный в `helpstringdll` атрибута и вызовы `DLLGetDocumentation` на этот DLL-файл с указанным контекстом и `lcid` атрибута.  
  
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
  
 При получении локализованных сведений с помощью атрибута `helpstringcontext` idl и `DLLGetDocumentation`реализовывать дополнительные интерфейсы не нужно.  
  
 Другим способом получения локализованного имени и описания свойства является реализация <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Дополнительные сведения, относящиеся к реализации этого метода см. в разделе [полей окна свойств и интерфейсы](../../extensibility/internals/properties-window-fields-and-interfaces.md).  

## <a name="see-also"></a>См. также  
 [Расширение свойств](../../extensibility/internals/extending-properties.md)