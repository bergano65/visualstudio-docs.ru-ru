---
title: Маршалинг параметров сборки взаимодействия Visual Studio | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: ac95c40b356c542da323a3ea3744827087f2d840
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686929"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Маршалинг параметров сборки взаимодействия Visual Studio
Пакеты VSPackage, написанные в управляемом коде, могут вызывать или вызываться неуправляемым кодом COM. Как правило, аргументы метода преобразуются или маршалируются автоматически маршалером взаимодействия. Однако иногда аргументы не могут быть преобразованы простым способом. В таких случаях параметры прототипа метода сборки взаимодействия используются для сопоставления параметров функции COM как можно точнее. Дополнительные сведения см. в разделе [Маршалинг взаимодействия](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Общие рекомендации  
  
##### <a name="read-the-reference-documentation"></a>Ознакомьтесь с справочной документацией  
 Эффективным способом обнаружения проблем взаимодействия является чтение справочной документации по каждому методу.  
  
 Справочная документация по каждому методу содержит три соответствующих раздела:  
  
- [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]Прототип функции COM.  
  
- Прототип метода сборки взаимодействия.  
  
- Список параметров COM и краткое описание каждого из них.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Поиск различий между двумя прототипами  
 Большинство проблем взаимодействия наследуются от несоответствий между определением определенного типа в COM-интерфейсе и определением того же типа в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] сборках взаимодействия. Например, рассмотрим различие в возможности передачи `null` значения в параметре [out]. Необходимо найти различия между двумя прототипами и рассмотреть их последствия для передаваемых данных.  
  
##### <a name="read-the-parameter-definitions"></a>Чтение определений параметров  
 Чтение определений параметров. Модель COM менее важна, чем среда CLR, связанная с смешением различных типов данных в одном параметре. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Интерфейсы COM полностью используют эту гибкость. Любой параметр, который может передавать или требовать нестандартное значение или тип данных, например постоянное значение в параметре указателя, должен быть описан в документации.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>Объекты IUnknown, переданные как тип void * *  
 Найдите параметры [out], которые определены как тип `void **` в COM-интерфейсе, но определены как `[``iid_is``]` в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] прототипе метода сборки взаимодействия.  
  
 Иногда COM-интерфейс создает `IUnknown` объект, а COM-интерфейс передает его как тип `void **` . Эти интерфейсы особенно важны, поскольку если переменная определена как [out] в IDL, то `IUnknown` объект подсчитывается по ссылке с помощью `AddRef` метода. Если объект не обрабатывается должным образом, происходит утечка памяти.  
  
> [!NOTE]
> `IUnknown`Объект, созданный COM-интерфейсом и возвращаемый в переменной [out], вызывает утечку памяти, если она не была явно освобождена.  
  
 Управляемые методы, обрабатывающие такие объекты, должны обрабатываться <xref:System.IntPtr> как указатель на `IUnknown` объект и вызывать <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> метод для получения объекта. Затем вызывающий объект должен привести возвращаемое значение к любому подходящему типу. Если объект больше не нужен, вызовите метод, <xref:System.Runtime.InteropServices.Marshal.Release%2A> чтобы освободить его.  
  
 Ниже приведен пример вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> метода и `IUnknown` правильной обработки объекта:  
  
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
> Для передачи `IUnknown` указателей объектов в качестве типа известны следующие методы <xref:System.IntPtr> . Обработайте их, как описано в этом разделе.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### <a name="optional-out-parameters"></a>Необязательные параметры [out]  
 Найдите параметры, которые определены как тип данных [out] ( `int` , `object` и т. д.) в com-интерфейсе, но они определены как массивы одного типа данных в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] прототипе метода сборки взаимодействия.  
  
 Некоторые COM-интерфейсы, такие как <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , обрабатывают [out] как необязательные. Если объект не является обязательным, эти COM-интерфейсы возвращают `null` указатель в качестве значения этого параметра вместо создания объекта [out]. Это сделано намеренно. Для этих интерфейсов `null` указатели предполагаются как часть правильного поведения VSPackage, и ошибка не возвращается.  
  
 Так как среда CLR не позволяет использовать значение параметра [out] `null` , часть спроектированного поведения этих интерфейсов не будет напрямую доступна в управляемом коде. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Методы сборки взаимодействия для затронутых интерфейсов обдействуются по этой причине, определяя соответствующие параметры в виде массивов, так как среда CLR допускает передачу `null` массивов.  
  
 Управляемые реализации этих методов должны `null` поставлять массив в параметр, когда ничего не возвращается. В противном случае создайте одноэлементный массив правильного типа и вставьте возвращаемое значение в массив.  
  
 Управляемые методы, получающие сведения из интерфейсов с необязательными параметрами [out], получают параметр в виде массива. Просто изучите значение первого элемента массива. Если это не так `null` , то следует считать первый элемент, как если бы он был исходным параметром.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Передача констант в параметрах указателя  
 Найдите параметры, которые определены как указатели [in] в COM-интерфейсе, но они определены как <xref:System.IntPtr> тип в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] прототипе метода сборки взаимодействия.  
  
 Аналогичная проблема возникает, когда COM-интерфейс передает специальное значение, например 0,-1 или – 2, вместо указателя на объект. В отличие от [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , среда CLR не позволяет приводить константы в качестве объектов. Вместо этого в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] сборке взаимодействия определяется параметр в виде <xref:System.IntPtr> типа.  
  
 Управляемые реализации этих методов должны использовать преимущества того факта, что у <xref:System.IntPtr> класса есть `int` и `void *` конструкторы, и, чтобы создать <xref:System.IntPtr> объект из объекта или целочисленной константы, в зависимости от ситуации.  
  
 Управляемые методы, получающие <xref:System.IntPtr> параметры этого типа, должны использовать <xref:System.IntPtr> Операторы преобразования типов для обработки результатов. Сначала преобразуйте <xref:System.IntPtr> в `int` и проверьте его на соответствие константам с соответствующими целочисленными значениями. Если значения не совпадают, преобразуйте их в объект требуемого типа и продолжайте.  
  
 Примеры см. в статьях <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>Возвращаемые значения OLE, переданные как параметры [out]  
 Ищите методы, которые имеют `retval` возвращаемое значение в COM-интерфейсе, но имеют `int` возвращаемое значение и дополнительный параметр массива [out] в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] прототипе метода сборки взаимодействия. Должно быть ясно, что для этих методов требуется специальная обработка, поскольку [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] прототипы методов сборки взаимодействия имеют еще один параметр, чем методы COM-интерфейса.  
  
 Многие COM-интерфейсы, которые работают с действиями OLE, отправляют сведения о состоянии OLE обратно в вызывающую программу, хранящуюся в `retval` возвращаемом значении интерфейса. Вместо использования возвращаемого значения соответствующие [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] методы сборки взаимодействия отправляют информацию обратно вызывающей программе, хранящейся в параметре массива [out].  
  
 Управляемые реализации этих методов должны создавать одноэлементный массив того же типа, что и параметр [out], и размещать его в параметре. Значение элемента массива должно совпадать с соответствующим COM-элементом `retval` .  
  
 Управляемые методы, вызывающие интерфейсы этого типа, должны извлечь первый элемент из массива [out]. Этот элемент можно рассматривать как `retval` возвращаемое значение из соответствующего COM-интерфейса.  
  
## <a name="see-also"></a>См. также:  
 [Маршалинг взаимодействия](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Маршалинг взаимодействия](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Устранение неполадок взаимодействия](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [Управляемые пакеты VSPackage](../misc/managed-vspackages.md)