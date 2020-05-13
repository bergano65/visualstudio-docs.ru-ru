---
title: Свойства оконных полей и интерфейсов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9529708c781e7fdb04c3b4c5ee143b7605857e84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706164"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
Модель выбора для определения того, какая информация отображается в окне **Свойств,** основана на окне, которое фокусируется в IDE. Каждое окно и объект в выбранном окне могут вынести объект контекста выбора в глобальный контекст выбора. Среда обновляет контекст глобального выбора значениями из оконной рамы, когда это окно имеет фокус. При изменении фокусировки меняется и контекст выбора.

## <a name="tracking-selection-in-the-ide"></a>Отслеживание выбора в IDE
 В оконной раме или сайте, принадлежащем <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>IDE, есть служба под названием . Следующие шаги показывают, как изменение в выборе, вызванное изменением фокуса на другое открытое окно или выбором другого элемента проекта в **Solution Explorer,** реализуется для изменения содержимого, отображаемого в окне **Свойств.**

1. Объект, созданный вашим VSPackage, который находится в <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> выбранных вызовах окна, чтобы <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> вызвать. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>

2. Контейнер выбора, предоставляемый выбранным окном, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> создает свой собственный объект. При изменении выбора VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> призывает уведомлять всех слушателей в среде, включая окно **Свойств,** об изменении. Он также предоставляет доступ к иерархии и информации о предметах, связанной с новым выбором.

3. Вызов <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> и передача его выбранным элементам `VSHPROPID_BrowseObject` иерархии <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> в параметре населяют объект.

4. Объект, полученный из [интерфейса IDispatch,](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) возвращается для [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) для запрошенного элемента, и окружающая <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> среда обертывает его в (см. следующий шаг). Если вызов не удается, среда `IVsHierarchy::GetProperty`делает второй вызов, передавая его контейнер выбора [__VSHPROPID. VSHPROPID_SelContainer,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) что элемент иерархии или элементы поставляются.

    Ваш проект VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> не создает, потому что окно VSPackage, поставляемое средой, которое реализует его (например, **Solution Explorer)** строится <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> от его имени.

5. Среда ссылается на методы <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> получения объектов на `IDispatch` основе интерфейса для заполнения окна **Свойств.**

   При изменении значения в окне **свойств** `IVsTrackSelectionEx::OnElementValueChangeEx` VSPackages реализуется и `IVsTrackSelectionEx::OnSelectionChangeEx` сообщает об изменении значения элемента. Затем среда ссылается <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> или сохраняет информацию, отображаемую в окне **Свойств,** синхронизированной со значениями свойств. Для получения дополнительной информации смотрите [Обновление значений свойств в окне свойств](#updating-property-values-in-the-properties-window).

   В дополнение к выбору другого элемента проекта в **Solution Explorer** для отображения свойств, связанных с этим элементом, можно также выбрать другой объект из окна формы или документа, используя список выпадающих данных, доступный в окне **Свойств.** Для получения дополнительной информации смотрите [список объектов окна свойств](../../extensibility/internals/properties-window-object-list.md).

   Вы можете изменить способ отображения информации в оконной сетке **Свойств** с алфавитного на категоричный, а при наличии — также открыть страницу свойств для выбранного объекта, нажав на соответствующие кнопки на окне **Свойств.** Для получения дополнительной информации смотрите [кнопки окна свойств](../../extensibility/internals/properties-window-buttons.md) и [страницы свойств](../../extensibility/internals/property-pages.md).

   Наконец, в нижней части окна **Свойств** также содержится описание поля, выбранного в сетке окна **Properties.** Для получения дополнительной [информации см.](#getting-field-descriptions-from-the-properties-window)

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a>Обновление значений свойств в окне свойств
Существует два способа поддерживать синхронизацию окна **Свойства** с изменениями значения свойства. Первый способ — вызывать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, который предоставляет доступ к базовым функциям окон, включая создание окон инструментов и документов, предоставляемых средой, и доступ к ним. Следующие шаги описывают этот процесс синхронизации.

### <a name="updating-property-values-using-ivsuishell"></a>Обновление значений свойств с помощью IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Обновление значений свойств с помощью интерфейса IVsUIShell

1. Вызывайте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (через службу <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>) каждый раз, когда пакетам VSPackage, проектам или редакторам необходимо создать или перечислить окна инструментов или документов.

2. Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> для синхронизации окна **Свойств** с изменениями свойств для проекта (или любого другого выбранного <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> объекта, просматриваемого окном **Свойств)** без реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> и выполнения событий.

3. Реализуйте методы <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> соответственно для установки и отключения уведомлений клиента о событиях иерархии, не требуя от иерархии реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.

### <a name="updating-property-values-using-iconnection"></a>Обновление значений свойств с помощью IConnection
 Второй способ поддерживать синхронизацию окна **Свойства** с изменениями значений свойств — реализовать `IConnection` в доступном для подключения объекте, чтобы указать наличие исходящих интерфейсов. Если требуется локализовать имя свойства, создайте производный объект из <xref:System.ComponentModel.ICustomTypeDescriptor>. Реализация <xref:System.ComponentModel.ICustomTypeDescriptor> может изменять возвращаемые дескрипторы свойств и имя свойства. Чтобы локализовать описание, создайте атрибут, который является производным от <xref:System.ComponentModel.DescriptionAttribute>, и переопределите свойство Description.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Рекомендации по реализации интерфейса IConnection

1. `IConnection` предоставляет доступ к подобъекту перечислителя с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Он также предоставляет доступ для всех подобъектов точки соединения, каждый из которых реализует интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.

2. Любой объект обзора отвечает за реализацию события <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. Окно **Свойства** будет содержать рекомендацию события, заданного через `IConnection`.

3. Точка подключения определяет, сколько подключений (одно или несколько) разрешено в его реализации <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Точка подключения, которая разрешает только один интерфейс, может возвращать <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> из метода <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.

4. Клиент может вызвать интерфейс `IConnection` для получения доступа к подобъекту перечислителя с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> затем можно вызвать для перечисления точек подключения для каждого исходящего идентификатора интерфейса (IID).

5. `IConnection` также можно вызывать для получения доступа к подобъектам точки подключения с интерфейсом <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> для каждого исходящего IID. Через <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> интерфейс клиент запускает или завершает консультативный цикл с подключаемым объектом и собственной синхронизацией клиента. Клиент также может <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> вызвать интерфейс, чтобы получить объект <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> регистратора с интерфейсом, чтобы перечислить соединения, о которымоня он знает.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a>Получение полевых описаний из окна свойств
В нижней части окна **Свойства** в области описания отображаются сведения, относящиеся к выбранному полю свойства. Эта функция включена по умолчанию. Если необходимо скрыть поле описания, правой кнопкой мыши щелкните окно **Свойства** и выберите пункт **Описание**. При этом также снимается флажок рядом с заголовком **Описание** в окне меню. Чтобы отобразить поле повторно, выполните те же действия для включения пункта **Описание** .

 Сведения в поле "Описание" поступают из <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Каждый метод, интерфейс, компонентный класс и т. д. может иметь нелокализованный атрибут `helpstring` в библиотеке типов. Окно **Свойства** извлекает строку из <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.

### <a name="to-specify-localized-help-strings"></a>Указание локализованных строк справки

1. Добавьте атрибут `helpstringdll` в инструкцию библиотеки в библиотеке типов (`typelib`).

   > [!NOTE]
   > Этот шаг является необязательным, если библиотека типов находится в файле библиотеки (OLB-файле).

2. Укажите атрибуты `helpstringcontext` для строк. Можно также указать атрибуты `helpstring` .

    Они отличаются от атрибутов `helpfile` и `helpcontext` , которые содержатся в реальных разделах справки в формате CHM.

   Для получения информации о описании, отображаемой <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> для имени выделенного свойства, окно `lcid` **Свойств** требует выбранного свойства с указанием желаемого атрибута для строки вывода. На внутреннем уровне <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> находит DLL-файл, указанный в атрибуте `helpstringdll`, и вызывает в этом файле метод `DLLGetDocumentation` с заданным контекстом и атрибутом `lcid`.

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

 Другим способом получения локализованного имени и описания свойства является реализация метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Дополнительные сведения, относящиеся к реализации этого метода, см. в статье [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>См. также

- [Расширение свойств](../../extensibility/internals/extending-properties.md)
