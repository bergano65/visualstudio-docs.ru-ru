---
title: Использование визуальной студии Interop сборки (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5926b2cce217565c889c7ef2eeef877691101ed6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704136"
---
# <a name="using-visual-studio-interop-assemblies"></a>Использование сборок взаимодействия Visual Studio
Interop сборки Visual Studio позволяют управляемым приложениям получить доступ к интерфейсам COM, которые обеспечивают расширяемость Visual Studio. Есть некоторые различия между прямыми интерфейсами COM и их интероп-версии. Например, HRESULT, как правило, представлены как значения int и должны обрабатываться так же, как исключения, а параметры (особенно из параметров) рассматриваются по-разному.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Обработка значений HRESULT, возвращаемых в управляемый код из COM
 При вызове COM-интерфейса из управляемого кода проверьте значение HRESULT и при необходимости создайте исключение. Класс <xref:Microsoft.VisualStudio.ErrorHandler> содержит метод <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, который создает исключение COM в зависимости от переданного ему значения HRESULT.

 По умолчанию метод <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> создает исключение каждый раз, когда ему передается значение HRESULT меньше нуля. В случаях, когда такие значения HRESULT являются допустимыми и исключения создавать не нужно, в <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> следует передать дополнительные значения HRESULT после их проверки. Если проверяемые значения HRESULT совпадают со значениями HRESULT, явно переданными в <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, исключение не создается.

> [!NOTE]
> Класс <xref:Microsoft.VisualStudio.VSConstants> содержит константы для общих <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>HRESULTS, например, и , и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS, например, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> и <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> также предоставляет методы <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> и <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, которые соответствуют макросам SUCCEEDED и FAILED в COM.

 Например, рассмотрим приведенный ниже вызов функции, в котором <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> является допустимым возвращаемым значением, но любое другое значение HRESULT меньше нуля представляет ошибку.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Если имеется несколько допустимых возвращаемых значений, дополнительные значения HRESULT можно просто добавить в список в вызове <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Возврат значений HRESULT в COM из управляемого кода
 Если исключений не возникает, управляемый код возвращает <xref:Microsoft.VisualStudio.VSConstants.S_OK> в вызвавшую его функцию COM. COM-взаимодействие поддерживает общие исключения, которые являются строго типизированными в управляемом коде. Например, метод, принимающий недопустимый аргумент `null`, вызывает исключение <xref:System.ArgumentNullException>.

 Если вы не знаете, какое именно исключение следует создать, но знаете, какое значение HRESULT нужно вернуть в COM, вы можете использовать метод <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> для создания соответствующего исключения. Такой подход работает и в случае с нестандартными ошибками, например <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. Метод <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> пытается сопоставить переданное ему значение HRESULT со строго типизированным исключением. Если это ему не удается, он создает универсальное исключение COM. Конечным результатом является то, что значение HRESULT, которое вы передали в <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> из управляемого кода, возвращается в вызвавшую этот код функцию COM.

> [!NOTE]
> Исключения снижают производительность и предназначены для указания на аномальные состояния программы. Часто наступающие условия следует обрабатывать внутри программы без создания исключений.

## <a name="iunknown-parameters-passed-as-type-void"></a>Параметры IUnknown, пройденных как Тип пустоты
 Ищите параметры, которые определяются `void **` как тип в интерфейсе COM, но которые определяются как `[``iid_is``]` в прототипе метода [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интероп сборки.

 Иногда интерфейс COM генерирует `IUnknown` объект, а интерфейс COM передает `void **`его как тип. Эти интерфейсы особенно важны, потому что если переменная определена `IUnknown` как «вне» `AddRef` в IDL, то объект рассчитывается с помощью метода. Утечка памяти происходит, если объект не обрабатывается правильно.

> [!NOTE]
> Объект, `IUnknown` созданный интерфейсом COM и возвращенный в переменную, вызывает утечку памяти, если он явно не выпущен.

 Управляемые методы обработки <xref:System.IntPtr> таких объектов должны `IUnknown` рассматриваться как <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> указатель на объект и вызывать метод для получения объекта. Затем вызывающее абонент должен отбросить значение возврата на любой тип, соответствующий. Когда объект больше не нужен, позвоните, <xref:System.Runtime.InteropServices.Marshal.Release%2A> чтобы освободить его.

 Ниже приводится пример <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> вызова метода `IUnknown` и правильной обработки объекта:

```
MyClass myclass;
Object object;
IntPtr pObj;
Guid iid = Typeof(MyClass).Guid;
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);
if (NativeMethods.Succeeded(hr))
{
    try
    {
        object = Marshal.GetObjectForIUnknown(pObj);
        myclass = object;
    }
    finally
    {
        Marshal.Release(pObj);
    }
}
else
{
    // error calling QueryViewInterface
}
```

> [!NOTE]
> Следующие методы, как `IUnknown` известно, передают <xref:System.IntPtr>указатели объектов как тип. Обработать их, как описано в этом разделе.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Дополнительные параметры
 Ищите параметры, которые определяются как тип`int` `object`данных (, и так далее) в интерфейсе COM, но [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] которые определяются как массивы одного и того же типа данных в прототипе метода интероп сборки.

 Некоторые интерфейсы COM, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>такие как, рассматривают параметры «out» как факультативные. Если объект не требуется, эти интерфейсы COM возвращают `null` указатель в качестве значения этого параметра вместо создания объекта. Это сделано намеренно. Для этих интерфейсов `null` указатели рассматриваются как часть правильного поведения VSPackage, и ошибка не возвращается.

 Поскольку CLR не позволяет значение параметра «вне» быть, `null`часть разработанного поведения этих интерфейсов не доступна непосредственно в управляемом коде. Методы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интероп-сборки для затронутых интерфейсов работают вокруг проблемы, определяя `null` соответствующие параметры как массивы, поскольку CLR позволяет передавать массивы.

 Управляемые реализации этих методов `null` должны поместить массив в параметр, когда нет ничего, чтобы быть возвращенным. В противном случае создайте одноэлементный массив правильного типа и поместите значение возврата в массив.

 Управляемые методы, которые получают информацию из интерфейсов с дополнительными параметрами ,out, получают параметр в виде массива. Достаточно изучить значение первого элемента массива. Если это `null`не так, относитесь к первому элементу так, как если бы это был первоначальный параметр.

## <a name="passing-constants-in-pointer-parameters"></a>Прохождение констант в параметрах указателя
 Ищите параметры, которые определяются как указатели в интерфейсе COM, <xref:System.IntPtr> но [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] которые определяются как тип в прототипе метода интероп сборки.

 Аналогичная проблема возникает, когда интерфейс COM проходит специальное значение, такое как 0, -1 или -2, вместо указателя объекта. В [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]отличие от, CLR не позволяет константы быть отлиты в качестве объектов. Вместо этого [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сборка interop определяет <xref:System.IntPtr> параметр как тип.

 Управляемые реализации этих методов должны использовать <xref:System.IntPtr> тот факт, `void *` что класс имеет <xref:System.IntPtr> как `int` и конструкторов для создания либо объекта или целых постоянных константы, по мере необходимости.

 Управляемые методы, которые получают <xref:System.IntPtr> параметры <xref:System.IntPtr> этого типа, должны использовать операторов преобразования типов для обработки результатов. Сначала преобразуйте <xref:System.IntPtr> `int` и протестуйте его против соответствующих констант. Если значения не совпадают, преобразуйте их в объект требуемого типа и продолжайте.

 Для примеров этого, увидеть <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.

## <a name="ole-return-values-passed-as-out-parameters"></a>Значения возврата OLE, передаваемые в качестве «из» параметров
 Ищите методы, `retval` которые имеют значение возврата в `int` интерфейсе COM, но имеют значение [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] возврата и дополнительный параметр массива в прототипе метода интероп сборки. Должно быть ясно, что эти методы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] требуют специальной обработки, поскольку прототипы метода интероп сборки имеют на один более параметр, чем методы интерфейса COM.

 Многие интерфейсы COM, которые имеют дело с деятельностью OLE, `retval` отправляют информацию о состоянии OLE обратно в программу вызова, хранящуюся в значении возврата интерфейса. Вместо использования значения возврата соответствующие [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] методы интероп-сборки отправляют информацию обратно в программу вызова, хранящуюся в параметре массива.

 Управляемые реализации этих методов должны создать одноэлементный массив того же типа, что и параметр «вне» и поместить его в параметр. Значение элемента массива должно быть таким `retval`же, как и соответствующий COM.

 Управляемые методы, вызывающие интерфейсы этого типа, должны вытащить первый элемент из массива. Этот элемент можно рассматривать как `retval` возвратное значение из соответствующего интерфейса COM.

## <a name="see-also"></a>См. также
- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)
