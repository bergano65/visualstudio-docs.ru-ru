---
title: "С помощью сборок взаимодействия Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 9762ba0404e739c167cadc3e9d3106c7f3ee14e8
ms.lasthandoff: 02/22/2017

---
# <a name="using-visual-studio-interop-assemblies"></a>С помощью Visual Studio сборки взаимодействия
Взаимодействия сборок Visual Studio позволяют управляемым приложениям доступ к COM-интерфейсы, позволяющие расширять Visual Studio. Существуют некоторые различия между прямой COM-интерфейсы и их взаимодействия версий. Например обычно представлены в виде значений типа int значений HRESULT и необходимо обрабатывать таким же образом, как исключения и параметры (особенно параметров out) обрабатываются по-разному.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Обработка значений HRESULT, возвращаемых в управляемый код из COM  
 При вызове COM-интерфейса из управляемого кода проверьте значение HRESULT и при необходимости создайте исключение. <xref:Microsoft.VisualStudio.ErrorHandler>Класс содержит <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>метод, который создает исключение COM, в зависимости от значения HRESULT, переданный на него.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> </xref:Microsoft.VisualStudio.ErrorHandler>  
  
 По умолчанию <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>создает исключение каждый раз, когда ему передается значение HRESULT, которое имеет значение меньше нуля.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> В случаях, когда такие значения HRESULT указаны допустимые значения и должен быть не исключение, следует передавать значения дополнительных значений HRESULT <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>после значения проверяются.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> Совпадения HRESULT тестируемой все значения HRESULT, явно переданных <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, исключение не возникает.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants>Класс содержит константы для общих значений HRESULT, например, <xref:Microsoft.VisualStudio.VSConstants.S_OK>и <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] значения HRESULT, например, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>и <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> </xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> </xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> </xref:Microsoft.VisualStudio.VSConstants.S_OK> </xref:Microsoft.VisualStudio.VSConstants> <xref:Microsoft.VisualStudio.VSConstants>также предоставляет <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A>и <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>методы, которые соответствуют макроса SUCCEEDED и сбой в COM.</xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> </xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A></xref:Microsoft.VisualStudio.VSConstants>  
  
 Например, рассмотрим следующий вызов функции, в котором <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>является приемлемым возвращаемое значение, но другие значения HRESULT меньше нуля представляет ошибку.</xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>  
  
 [!code-vb[#1 VSSDKHRESULTInformation](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb) ] 
 [!code-cs [VSSDKHRESULTInformation&#1;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 Если имеются несколько допустимых возвращаемых значений, дополнительные значения HRESULT просто могут быть добавлены в список в вызове <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>  
  
 [!code-vb[VSSDKHRESULTInformation&2;](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb) ] 
 [!code-cs [VSSDKHRESULTInformation&#2;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Возврат значений HRESULT в COM из управляемого кода  
 Если исключение не возникает, управляемый код возвращает <xref:Microsoft.VisualStudio.VSConstants.S_OK>функции COM, вызвавший его.</xref:Microsoft.VisualStudio.VSConstants.S_OK> COM-взаимодействие поддерживает общие исключения, которые являются строго типизированными в управляемом коде. Например, метод, принимающий неприемлемо `null` аргумент, создает исключение <xref:System.ArgumentNullException>.</xref:System.ArgumentNullException>  
  
 Если нет уверенности, какие исключения, но известно значение HRESULT требуется вернуть COM, можно использовать <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>метода вызывает соответствующее исключение.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Это работает даже с нестандартные ошибки, например, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>пытается сопоставить значение HRESULT передается его строго типизированный исключение.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Если это ему не удается, он создает универсальное исключение COM. Конечный результат заключается в значение HRESULT передачи возвращены <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>из управляемого кода в функцию COM, вызвавший его.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>  
  
> [!NOTE]
>  Исключения снижают производительность и предназначены для указания на аномальные состояния программы. Часто наступающие условия следует обрабатывать внутри программы без создания исключений.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown параметров, передаваемых в качестве типа void **  
 Поиск [параметров, которые определены как тип out] `void **` в модели COM интерфейс, но определяются как `[``iid_is``]` в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототип метода сборку взаимодействия.  
  
 Иногда интерфейс COM создает `IUnknown` объекта и COM-интерфейса затем передает его в качестве типа `void **`. Эти интерфейсы являются особенно важно, поскольку если переменная определена как [out] в IDL-ФАЙЛЕ, то `IUnknown` объекта подсчетом ссылок с `AddRef` метод. Если объект обрабатывается неправильно, возникает утечка памяти.  
  
> [!NOTE]
>  `IUnknown` Объект создается с помощью интерфейса COM и возвращается в переменной [out] вызывает утечку памяти, если явно не освобождается.  
  
 Управляемые методы, обрабатывающие такие объекты следует рассматривать <xref:System.IntPtr>как указатель на `IUnknown` и вызовите <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>метод для получения объекта.</xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> </xref:System.IntPtr> Вызывающий объект должен затем привести возвращаемое значение для любой тип подходит. Когда объект больше не нужен, вызов <xref:System.Runtime.InteropServices.Marshal.Release%2A>отпустите его.</xref:System.Runtime.InteropServices.Marshal.Release%2A>  
  
 Ниже приведен пример вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>метод и обработка `IUnknown` объекта правильно:</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
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
>  Для передачи известны следующие методы `IUnknown` объекта указатели как тип <xref:System.IntPtr>.</xref:System.IntPtr> Обработайте их, как описано в этом разделе.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>Необязательные [параметры out]  
 Поиск параметров, которые определяются как [out] тип данных (`int`, `object`и так далее) в COM интерфейс, но определяются как массивы тот же тип данных, в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототип метода сборку взаимодействия.  
  
 Некоторые COM интерфейсы, такие как <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, обрабатывать [необязательные параметры out].</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> Если объект не требуется, возвращают данные COM-интерфейсы `null` в качестве значения этого параметра вместо создания объекта [out] указатель. Это сделано намеренно. Для этих интерфейсов `null` указатели считаются частью VSPackage правильное поведение, и никакие ошибки не возвращаются.  
  
 Поскольку среда CLR не допускает значение параметр [out] `null`, часть предусмотрено для сохранения этих интерфейсов нет прямого доступа в рамках управляемого кода. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Методы сборки взаимодействия для затронутых интерфейсов решить эту проблему, определив соответствующие параметры как массивы, так как среда CLR позволяет передавать `null` массивов.  
  
 Управляемые реализации этих методов следует поместить `null` массив в качестве параметра, когда не возвращается. В противном случае — создать одноэлементный массив соответствующего типа и поместить возвращаемое значение в массиве.  
  
 Управляемые методы для получения информации из интерфейсов с необязательным [out] Параметры получает параметр в виде массива. Достаточно проверьте значение первого элемента массива. Если это не `null`, рассматривает первого элемента так же, как исходный параметр.  
  
## <a name="passing-constants-in-pointer-parameters"></a>Передача константы в параметры-указатели  
 Найдите параметры, определенные как [в] указатели в COM-интерфейса, которые определены как <xref:System.IntPtr>введите [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототип метода сборку взаимодействия.</xref:System.IntPtr>  
  
 Такая же проблема возникает при COM-интерфейса передает специальное значение, например 0, -1 или – 2, а не указатель на объект. В отличие от [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], среда CLR не допускает константы для приведения как объекты. Вместо этого [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сборки взаимодействия определяет в качестве параметра <xref:System.IntPtr>тип.</xref:System.IntPtr>  
  
 Управляемые реализации этих методов следует воспользоваться тем, <xref:System.IntPtr>класс имеет оба `int` и `void *` конструкторы для создания <xref:System.IntPtr>из объекта или целая константа в соответствии с потребностями.</xref:System.IntPtr> </xref:System.IntPtr>  
  
 Управляемые методы, которые получают <xref:System.IntPtr>Параметры этого типа следует использовать <xref:System.IntPtr>Введите операторы преобразования для обработки результатов.</xref:System.IntPtr> </xref:System.IntPtr> Сначала преобразовать <xref:System.IntPtr>для `int` и проверить соответствующие целочисленных констант.</xref:System.IntPtr> Если значения не совпадают, преобразовать его в объект нужного типа и продолжить.  
  
 В качестве примера в разделе <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE возвращают значения передаются как [параметры out]  
 Поиск методов, которые имеют `retval` возвращаемое значение в интерфейсе COM, однако, иметь `int` возвращаемое значение и дополнительный [параметр массива в out] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототип метода сборку взаимодействия. Следует учитывать, что эти методы требуют специальной обработки, поскольку [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] еще один параметр, чем методы интерфейса COM имеют прототипы метод сборки взаимодействия.  
  
 Многие интерфейсы COM, связанные с действием OLE отправить сведения о состоянии OLE обратно вызывающей программе, хранящиеся в `retval` возвращаемое значение интерфейса. Вместо того чтобы использовать возвращаемое значение, соответствующее [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] методы сборки взаимодействия отправить данные обратно в вызывающей программе, хранящихся в [out] массив параметров.  
  
 Управляемые реализации этих методов необходимо создать одноэлементный массив одного типа в качестве параметра [out] и поместить его в качестве параметра. Значение элемента массива должно быть таким же, как соответствующие COM `retval`.  
  
 Управляемые методы, которые вызывают интерфейсы этого типа следует извлекать первый элемент из массива [out]. Этот элемент можно рассматривать как будто `retval` возвращаемое значение от соответствующего COM-интерфейса.  
  
## <a name="see-also"></a>См. также  
 [Взаимодействие с неуправляемым кодом](http://msdn.microsoft.com/Library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
