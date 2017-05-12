---
title: "Как: использование журнала действий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
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
ms.sourcegitcommit: c9df048a49580f3526b48e29041ef3758722ed27
ms.openlocfilehash: dc821f22a04432989a2edb68c483d298ffcf0eb7
ms.lasthandoff: 05/03/2017

---
# <a name="how-to-use-the-activity-log"></a>Как: использование журнала действий
Пакеты VSPackage может записать события в журнал действий. Эта функция особенно полезна для отладки пакетов VSPackage в средах розничной торговли.  
  
> [!TIP]
>  Журнал действий всегда включен. Visual Studio сохраняет буфер последовательного последние 100 записей, а также первых десяти операций, которые имеют общих сведений о настройке.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Для записи в журнал действий  
  
1.  Вставьте этот код в метод < xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A > или любого другого метода, кроме конструктора VSPackage:  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Этот код получает службу < xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog > и приводит его к интерфейсу < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog >. < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A > записывает информационное запись в журнал действий с использованием текущего контекста культуры.  
  
2.  При загрузке VSPackage (обычно при вызове команды или открытии окна) текст записывается в журнал действий.  
  
### <a name="to-examine-the-activity-log"></a>Для просмотра журнала активности  
  
1.  Поиск данных в Visual Studio журнал действий во вложенной папке: *% AppData %*\Microsoft\VisualStudio\15.0\ActivityLog.XML...  
  
2.  Откройте журнал действий в любом текстовом редакторе. Ниже приведен типичный запись.  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Поскольку журнал действий — это служба, журнал действий недоступна в конструкторе пакета VSPackage.  
  
 Журнал действий должен быть получен непосредственно перед записью на него. Не кэшировать или сохранить журнал действий для использования в будущем.  
  
## <a name="see-also"></a>См. также  
 < xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog >   
 < xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE >   
 [Устранение неполадок пакетов VSPackage](../extensibility/troubleshooting-vspackages.md)   
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)

