---
title: С помощью сборок взаимодействия Visual Studio | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff9ce80d9c0988d38dfe86e193e8390b4719cbcb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429623"
---
# <a name="using-visual-studio-interop-assemblies"></a>Использование сборок взаимодействия Visual Studio
Visual Studio взаимодействия сборки позволяют управляемые приложения для доступа к COM-интерфейсы, позволяющие расширять Visual Studio. Существуют некоторые различия между прямой COM-интерфейсы и их взаимодействия версий. Например сопоставление значений HRESULT, обычно представлены в виде значений типа int и необходимо обрабатывать в так же, как исключения и параметры (особенно выходных параметров) обрабатываются по-разному.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Обработка значений HRESULT, возвращаемых в управляемый код из COM
 При вызове COM-интерфейса из управляемого кода проверьте значение HRESULT и при необходимости создайте исключение. Класс <xref:Microsoft.VisualStudio.ErrorHandler> содержит метод <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, который создает исключение COM в зависимости от переданного ему значения HRESULT.

 По умолчанию метод <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> создает исключение каждый раз, когда ему передается значение HRESULT меньше нуля. В случаях, когда такие значения HRESULT являются допустимыми и исключения создавать не нужно, в <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> следует передать дополнительные значения HRESULT после их проверки. Если проверяемые значения HRESULT совпадают со значениями HRESULT, явно переданными в <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, исключение не создается.

> [!NOTE]
> <xref:Microsoft.VisualStudio.VSConstants> Класс содержит константы для общих значений HRESULT, например, <xref:Microsoft.VisualStudio.VSConstants.S_OK> и <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] значения HRESULT, например, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> и <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> также предоставляет методы <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> и <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, которые соответствуют макросам SUCCEEDED и FAILED в COM.

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

## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown параметров, передаваемых в качестве типа void **
 Поиск [параметров, которые определены как тип out] `void **` в модели COM интерфейс, но, определяются как `[``iid_is``]` в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототип метода сборки взаимодействия.

 В некоторых случаях COM-интерфейс приводит к возникновению ошибки `IUnknown` объекта и COM-интерфейса затем передает его в качестве типа `void **`. Эти интерфейсы являются особенно важно, поскольку если переменная определена как [out] в IDL-ФАЙЛЕ, то `IUnknown` объект с подсчетом ссылок с `AddRef` метод. Если объект обрабатывается неправильно, возникает утечка памяти.

> [!NOTE]
> `IUnknown` Объекта создается с COM-интерфейса и возвращается в переменную [out] вызывает утечку памяти, если он не освобождается явно.

 Управляемые методы, обрабатывающие такие объекты следует относиться <xref:System.IntPtr> как указатель на `IUnknown` объекта и вызовите <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> метод для получения объекта. Вызывающий объект затем необходимо привести возвращаемое значение к любой из этих типов. Когда объект больше не нужен, вызовите <xref:System.Runtime.InteropServices.Marshal.Release%2A> для его освобождения.

 Ниже приведен пример вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> метод и обработка `IUnknown` объекта правильно:

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
> Следующие методы известны для передачи `IUnknown` объекта указатели как тип <xref:System.IntPtr>. Их необходимо обработайте, как описано в этом разделе.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Необязательные [параметры out]
 Найдите параметры, которые определяются как [out] тип данных (`int`, `object`, и так далее) в модели COM интерфейс, но, определяются как массивы одного типа данных в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототип метода сборки взаимодействия.

 Некоторые COM интерфейсы, такие как <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, обрабатывать [out] Параметры как необязательные. Если объект не требуется, возвращают данные COM-интерфейсы `null` указатель в качестве значения этого параметра вместо создания [out] объект. Это сделано намеренно. Для этих интерфейсов `null` указатели считаются как часть правильное поведение пакета VSPackage, и никакие ошибки не возвращаются.

 Поскольку среда CLR не поддерживает значение параметра [out] быть `null`, часть предусмотрено для сохранения этих интерфейсов не является напрямую доступен в рамках управляемого кода. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Методы сборки взаимодействия для затронутых решить эту проблему путем определения соответствующих параметров как массивы, поскольку среда CLR позволяет передачу `null` массивов.

 Управляемые реализации этих методов следует помещать `null` массива в качестве параметра при отсутствии ничего не возвращается. В противном случае создайте одноэлементный массив соответствующего типа и поместите возвращаемое значение в массиве.

 Управляемые методы для получения сведений из интерфейсов с необязательным [out] Параметры получает параметр в виде массива. Просто проверьте значение первого элемента массива. Если это не `null`, обрабатывать первого элемента так же, как исходный параметр.

## <a name="passing-constants-in-pointer-parameters"></a>Передача константы в параметры-указатели
 Найдите параметры, определенные как [in] указатели в COM-интерфейса, однако, определяются как <xref:System.IntPtr> введите [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототип метода сборки взаимодействия.

 Аналогичная проблема возникает, когда COM-интерфейс передает специальное значение, например 0, -1 или -2, а не указатель объекта. В отличие от [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], среда CLR не поддерживает константы для приведения как объекты. Вместо этого [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сборку взаимодействия определяет параметр как <xref:System.IntPtr> типа.

 Управляемые реализации этих методов следует воспользоваться тот факт, <xref:System.IntPtr> класс имеет оба `int` и `void *` конструкторы для создания <xref:System.IntPtr> из объекта или целой константой в соответствии с потребностями.

 Управляемые методы, которые получают <xref:System.IntPtr> параметры этого типа следует использовать <xref:System.IntPtr> введите операторы преобразования для обработки результатов. Сначала преобразуйте <xref:System.IntPtr> для `int` и его проверка относительно соответствующих целочисленные константы. Если значения не совпадают, преобразовать его в объект нужного типа и продолжить.

 В качестве примера, см. в разделе <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE возвращают значения, переданные как [параметры out]
 Поиск методов, которые имеют `retval` возвращаемое значение в COM-интерфейса, однако, иметь `int` возвращаемое значение и дополнительный [параметру-массиву в out] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототип метода сборки взаимодействия. Следует четко понимать, что эти методы требуют специальной обработки, так как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототипы метод сборку взаимодействия имеют один параметр больше, чем методы интерфейса COM.

 Многие COM-интерфейсы, которые имеют дело с действием OLE сведения о состоянии OLE обратной отправки вызывающей программе, хранящиеся в `retval` возвращаемое значение интерфейса. Вместо того чтобы использовать возвращаемое значение, соответствующее [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] методы сборки взаимодействия отправляет данные обратно вызывающей программе, хранящиеся в [out] массив параметров.

 Управляемые реализации этих методов необходимо создать одноэлементный массив одного типа в качестве параметра [out] и поместить его в параметре. Значение элемента массива должен быть таким же, как соответствующие COM `retval`.

 Управляемые методы, которые вызывают интерфейсы этого типа следует извлечь первый элемент из массива [out]. Этот элемент может рассматриваться как будто `retval` возвращаемое значение из соответствующего COM-интерфейса.

## <a name="see-also"></a>См. также
- [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)