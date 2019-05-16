---
title: Параметров сборки взаимодействия Visual Studio маршалинг | Документация Майкрософт
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686929"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Маршалинг параметров сборки взаимодействия Visual Studio
Пакеты VSPackage, написаны в управляемом коде может возникнуть необходимость вызвать либо вызываться неуправляемым кодом COM. Как правило аргументы метода преобразования или маршалинга, автоматически, упаковщик взаимодействия. Тем не менее иногда аргументы нельзя преобразовать простым способом. В таких случаях параметры прототип метода сборки взаимодействия, используются для сопоставления параметров функции COM как можно точнее. Дополнительные сведения см. в разделе [маршалинг взаимодействия](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Общие рекомендации  
  
##### <a name="read-the-reference-documentation"></a>См. справочную информацию  
 Эффективный способ обнаружения проблем взаимодействия является см. справочную информацию для каждого метода.  
  
 Справочная документация для каждого метода содержит три соответствующие разделы:  
  
- [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] COM прототип функции.  
  
- Прототип метода сборки взаимодействия.  
  
- Список параметров COM и краткое описание каждого из них.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Поиск различий между двумя прототипов  
 Большинство проблем взаимодействия являются производными от несоответствия между определением определенного типа в COM-интерфейса и определение одного типа в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] сборок взаимодействия. Например, обратите внимание на разницу в также возможность передавать `null` значение параметра [out]. Необходимо искать различия между двумя прототипы и рассмотрите возможность их последствия для передаваемых данных.  
  
##### <a name="read-the-parameter-definitions"></a>Чтение определения параметров  
 Чтение определения параметров. COM является менее строгие, чем среда CLR (CLR) о смешать различные типы данных в одном параметре. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] COM-интерфейсы воспользоваться всеми преимуществами этой гибкости. Любой параметр, который можно передать или требуется нестандартное значение или тип данных, например постоянного значения в параметр-указатель, должны быть описаны в документации по таким образом.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>IUnknown-объекты, передаваемые как тип void **  
 Поиск [параметров, которые определены как тип out] `void **` в модели COM интерфейс, но, определяются как `[``iid_is``]` в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] прототип метода сборки взаимодействия.  
  
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
  
### <a name="optional-out-parameters"></a>Необязательные [параметры out]  
 Найдите параметры, которые определяются как [out] тип данных (`int`, `object`, и так далее) в модели COM интерфейс, но, определяются как массивы одного типа данных в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] прототип метода сборки взаимодействия.  
  
 Некоторые COM интерфейсы, такие как <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, обрабатывать [out] Параметры как необязательные. Если объект не требуется, возвращают данные COM-интерфейсы `null` указатель в качестве значения этого параметра вместо создания [out] объект. Это сделано намеренно. Для этих интерфейсов `null` указатели считаются как часть правильное поведение пакета VSPackage, и никакие ошибки не возвращаются.  
  
 Поскольку среда CLR не поддерживает значение параметра [out] быть `null`, часть предусмотрено для сохранения этих интерфейсов не является напрямую доступен в рамках управляемого кода. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Методы сборки взаимодействия для затронутых решить эту проблему путем определения соответствующих параметров как массивы, поскольку среда CLR позволяет передачу `null` массивов.  
  
 Управляемые реализации этих методов следует помещать `null` массива в качестве параметра при отсутствии ничего не возвращается. В противном случае создайте одноэлементный массив соответствующего типа и поместите возвращаемое значение в массиве.  
  
 Управляемые методы для получения сведений из интерфейсов с необязательным [out] Параметры получает параметр в виде массива. Просто проверьте значение первого элемента массива. Если это не `null`, обрабатывать первого элемента так же, как исходный параметр.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Передача константы в параметры-указатели  
 Найдите параметры, определенные как [in] указатели в COM-интерфейса, однако, определяются как <xref:System.IntPtr> введите [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] прототип метода сборки взаимодействия.  
  
 Аналогичная проблема возникает, когда COM-интерфейс передает специальное значение, например 0, -1 или – 2, а не указатель объекта. В отличие от [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], среда CLR не поддерживает константы для приведения как объекты. Вместо этого [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] сборку взаимодействия определяет параметр как <xref:System.IntPtr> типа.  
  
 Управляемые реализации этих методов следует воспользоваться тот факт, <xref:System.IntPtr> класс имеет оба `int` и `void *` конструкторы для создания <xref:System.IntPtr> из объекта или целой константой в соответствии с потребностями.  
  
 Управляемые методы, которые получают <xref:System.IntPtr> параметры этого типа следует использовать <xref:System.IntPtr> введите операторы преобразования для обработки результатов. Сначала преобразуйте <xref:System.IntPtr> для `int` и его проверка относительно соответствующих целочисленные константы. Если значения не совпадают, преобразовать его в объект нужного типа и продолжить.  
  
 В качестве примера, см. в разделе <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>OLE возвращают значения, переданные как [параметры out]  
 Поиск методов, которые имеют `retval` возвращаемое значение в COM-интерфейса, однако, иметь `int` возвращаемое значение и дополнительный [параметру-массиву в out] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] прототип метода сборки взаимодействия. Следует четко понимать, что эти методы требуют специальной обработки, так как [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] прототипы метод сборку взаимодействия имеют один параметр больше, чем методы интерфейса COM.  
  
 Многие COM-интерфейсы, которые имеют дело с действием OLE сведения о состоянии OLE обратной отправки вызывающей программе, хранящиеся в `retval` возвращаемое значение интерфейса. Вместо того чтобы использовать возвращаемое значение, соответствующее [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] методы сборки взаимодействия отправляет данные обратно вызывающей программе, хранящиеся в [out] массив параметров.  
  
 Управляемые реализации этих методов необходимо создать одноэлементный массив одного типа в качестве параметра [out] и поместить его в параметре. Значение элемента массива должен быть таким же, как соответствующие COM `retval`.  
  
 Управляемые методы, которые вызывают интерфейсы этого типа следует извлечь первый элемент из массива [out]. Этот элемент может рассматриваться как будто `retval` возвращаемое значение из соответствующего COM-интерфейса.  
  
## <a name="see-also"></a>См. также  
 [Маршалинг взаимодействия](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Маршалинг взаимодействия](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Устранение неполадок взаимодействия](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [Управляемые пакеты VSPackage](../misc/managed-vspackages.md)