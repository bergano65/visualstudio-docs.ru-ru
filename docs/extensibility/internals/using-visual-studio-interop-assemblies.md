---
title: "С помощью сборок взаимодействия Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 98d579755190eaf51448ef2b1b855c087bcad358
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="using-visual-studio-interop-assemblies"></a>С помощью сборок взаимодействия Visual Studio
Visual Studio взаимодействия сборки позволяют управляемых приложений для доступа к COM-интерфейсы, которые обеспечивают расширяемость Visual Studio. Существуют некоторые различия между прямой COM-интерфейсы и их версиями, взаимодействия. Например обычно представлены в виде значений типа int значений HRESULT и необходимо обрабатывать таким же образом, как исключения и параметры (особенно параметры out) обрабатываются по-разному.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Обработка значений HRESULT, возвращаемых в управляемый код из COM  
 При вызове COM-интерфейса из управляемого кода проверьте значение HRESULT и при необходимости создайте исключение. <xref:Microsoft.VisualStudio.ErrorHandler> Класс содержит <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> переданного ему метод, который создает исключение COM, в зависимости от значения HRESULT.  
  
 По умолчанию <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> создает исключение каждый раз, когда ему передается значение HRESULT, который имеет значение меньше нуля. В случаях, когда такие HRESULT являются допустимыми и не создавалось исключение, должны быть переданы дополнительные значения HRESULT <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> после проверяются значения. Если проверяемые значения HRESULT совпадает со значениями HRESULT, явно переданных <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, исключение не возникает.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> Класс содержит константы для общих значений HRESULT, например, <xref:Microsoft.VisualStudio.VSConstants.S_OK> и <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] значения HRESULT, например, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> и <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants>также предоставляет <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> и <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> методы, которые соответствуют макросы SUCCEEDED и FAILED в COM.  
  
 Например, рассмотрим следующий вызов функции, в котором <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> является допустимым возвращаемым значением, но любое другое значение HRESULT меньше нуля представляет ошибку.  
  
 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 Если имеются несколько допустимых возвращаемых значений, дополнительные значения HRESULT можно просто добавить в список в вызове <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Возврат значений HRESULT в COM из управляемого кода  
 Если исключение не возникает, управляемый код возвращает <xref:Microsoft.VisualStudio.VSConstants.S_OK> для COM-функция, который вызвал его. COM-взаимодействие поддерживает общие исключения, которые являются строго типизированными в управляемом коде. Например, метод, принимающий недопустимый `null` возникает исключение аргумента <xref:System.ArgumentNullException>.  
  
 Если достоверно неизвестно, какие исключения, но известно значение HRESULT, который вы хотите вернуть в COM, можно использовать <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> метод для создания соответствующего исключения. Это работает даже с нестандартными ошибками, например, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>пытается сопоставить значение HRESULT переданное ему значение со строго типизированным исключением. Если это ему не удается, он создает универсальное исключение COM. Конечным результатом является то, что значение HRESULT передается <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> из управляемого кода возвращается функция COM, который вызвал его.  
  
> [!NOTE]
>  Исключения снижают производительность и предназначены для указания на аномальные состояния программы. Часто наступающие условия следует обрабатывать внутри программы без создания исключений.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown параметров, передаваемых в качестве типа void **  
 Поиск [параметров, которые определены как тип out] `void **` в COM интерфейс, но определяются как `[``iid_is``]` в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототипа сборку взаимодействия.  
  
 В некоторых случаях это COM-интерфейс приводит к возникновению ошибки `IUnknown` объекта и COM-интерфейса затем передает его в качестве типа `void **`. Эти интерфейсы являются особенно важно, поскольку если переменная определена как [out] в IDL-ФАЙЛЕ, то `IUnknown` объекта учитывается при подсчете ссылок с `AddRef` метод. Утечка памяти происходит, если объект не обрабатывается правильно.  
  
> [!NOTE]
>  `IUnknown` Объект создается с помощью интерфейса COM и возвращается в переменной [out] вызывает утечку памяти, если явно не освобождается.  
  
 Управляемые методы, обрабатывающие таких объектов должно рассматривать <xref:System.IntPtr> как указатель на `IUnknown` объекта и вызвать <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> метод для получения объекта. Вызывающий объект затем следует привести возвращаемое значение для любого из этих типов. Когда объект больше не нужен, вызов <xref:System.Runtime.InteropServices.Marshal.Release%2A> для его освобождения.  
  
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
>  Для передачи известны следующие методы `IUnknown` объекта указатели как тип <xref:System.IntPtr>. Их необходимо обработайте, как описано в этом разделе.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>Необязательные [параметры out]  
 Поиск параметров, которые определены как [out] тип данных (`int`, `object`и так далее) в COM интерфейс, но определяются как массивы того же типа данных в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототипа сборку взаимодействия.  
  
 Некоторые COM интерфейсы, такие как <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, обрабатывать [необязательные параметры out]. Если объект не является обязательной, возвращают данные COM-интерфейсы `null` указатель в качестве значения этого параметра вместо создания [out] объект. Это сделано намеренно. Для этих интерфейсов `null` указатели считаются как часть правильное поведение VSPackage, и никакие ошибки не возвращаются.  
  
 Поскольку среда CLR не допускает значение параметром [out] быть `null`, часть предусмотрено для сохранения этих интерфейсов не является напрямую доступен в рамках управляемого кода. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Методы сборки взаимодействия для затронутых обойти эту проблему путем определения соответствующие параметры в виде массивов, так как среда CLR позволяет передавать `null` массивов.  
  
 Управляемые реализации этих методов следует помещать `null` массив в качестве параметра, если ничего не возвращается. В противном случае создайте одноэлементному массиву правильного типа и сохраните возвращаемое значение в массиве.  
  
 Управляемые методы для получения сведений из интерфейсов с необязательным [out] Параметры получают параметр как массив. Достаточно проверьте значение первого элемента массива. Если это не `null`, обрабатывать первого элемента, как если бы это был исходный параметр.  
  
## <a name="passing-constants-in-pointer-parameters"></a>Передача констант в параметры-указатели  
 Найдите параметры, определенные как [в] указателей в COM-интерфейса, но которые определены как <xref:System.IntPtr> введите [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототипа сборку взаимодействия.  
  
 Аналогичная проблема возникает в случае COM-интерфейс передает специальные значения, например 0, -1 или -2, а не указатель на объект. В отличие от [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], среда CLR не допускает константы, рассматриваемые как объекты. Вместо этого [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сборки взаимодействия определяет параметр как <xref:System.IntPtr> типа.  
  
 Управляемые реализации этих методов необходимо пользоваться преимуществами тот факт, <xref:System.IntPtr> класс имеет оба `int` и `void *` конструкторы для создания <xref:System.IntPtr> из объекта или целой константой в соответствии с потребностями.  
  
 Управляемые методы, которые получают <xref:System.IntPtr> параметры этого типа следует использовать <xref:System.IntPtr> введите операторы преобразования для обработки результатов. Сначала преобразовать <xref:System.IntPtr> для `int` и его проверка относительно соответствующих целочисленных констант. Если значения не совпадают, преобразовать его в объект нужного типа и продолжить.  
  
 В качестве примера, в разделе <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE возвращают значения, переданные как [параметры out]  
 Искать методы, которые имеют `retval` возвращаемое значение в COM-интерфейса, но имеют `int` возвращаемое значение и дополнительный [параметр массива в out] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототипа сборку взаимодействия. Следует учитывать, что эти методы требуют специальной обработки, так как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] прототипы метод сборки взаимодействия имеют один параметр более чем методы интерфейса COM.  
  
 Многие COM-интерфейсы, связанные с операцией OLE отправит сведения о состоянии OLE вызывающей программе, хранящиеся в `retval` возвращаемое значение интерфейса. Вместо того чтобы использовать возвращаемое значение, соответствующее [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] методы сборки взаимодействия отправить данные обратно в вызывающей программе, хранящихся в [out] массив параметров.  
  
 Управляемые реализации этих методов необходимо создать одноэлементный массив того же типа как параметр [out] и поместить его в параметре. Значение элемента массива должен быть таким же, как соответствующие COM `retval`.  
  
 Управляемые методы, которые вызывают интерфейсы этого типа следует извлечь первый элемент из массива [out]. Этот элемент может обрабатываться, как если бы он был `retval` возвращаемое значение из соответствующего COM-интерфейса.  
  
## <a name="see-also"></a>См. также  
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)