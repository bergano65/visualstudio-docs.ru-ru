---
title: 'Как: использование журнала действий | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6200c5e71054c6132d9239769d354bfd32703fb0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-the-activity-log"></a>Как: использование журнала действий
Пакеты VSPackage может записать события в журнал действий. Эта функция особенно полезна для отладки пакетов VSPackage в средах розничной торговли.  
  
> [!TIP]
>  Журнал действий всегда включен. Visual Studio сохраняет буфер последовательного последние 100 записей, а также первые 10 операций, которые имеют общих сведений о настройке.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Для записи в журнал действий  
  
1.  Вставьте этот код в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метода или в любой другой метод, кроме конструктора VSPackage:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Этот код получает <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> службы и приводит его к <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейса. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Записывает информационное запись в журнал действий с использованием текущего контекста культуры.  
  
2.  При загрузке VSPackage (обычно при вызове команды или открытии окна) текст записывается в журнал действий.  
  
### <a name="to-examine-the-activity-log"></a>Для просмотра журнала активности  
  
1.  Запустите Visual Studio с [/Log](../ide/reference/log-devenv-exe.md) переключатель командной строки для записи ActivityLog.xml на диск во время сеанса.

2.  После закрытия Visual Studio, поиск журнал действий во вложенной папке данных Visual Studio: *% AppData %*\Microsoft\VisualStudio\15.0\ActivityLog.xml.  
  
3.  Откройте журнал действий в любом текстовом редакторе. Ниже приведен типичный запись.  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Поскольку журнал действий — это служба, журнал действий недоступна в конструкторе пакета VSPackage.  
  
 Журнал действий должен быть получен непосредственно перед записью на него. Не кэшировать или сохранить журнал действий для использования в будущем.  
  
## <a name="see-also"></a>См. также
 [/ Log (devenv.exe)](../ide/reference/log-devenv-exe.md)   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Устранение неполадок пакетов VSPackage](../extensibility/troubleshooting-vspackages.md)   
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)
