---
title: "Практическое руководство: использование журнала действий | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Пакеты VSPackage, отладка"
  - "Пакеты VSPackage, устранение неполадок"
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: использование журнала действий
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Сообщения в журнале действий можно написать пакеты VSPackage. Эта функция особенно полезна для отладки пакетов VSPackages на предприятиях розничной торговли.  
  
> [!TIP]
>  Журнал действий всегда включен. Visual Studio сохраняет скользящий буфер последние 100 записей, а также первые десять записей, имеющих общих сведений о настройке.  
  
### Для записи в журнал действий  
  
1.  Вставьте этот код в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метода или в любой другой метод, за исключением VSPackage конструктора:  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Этот код получает <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> службы и приводит его к <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейс.<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Записывает информационное запись в журнал действий, с использованием текущего контекста культуры.  
  
2.  При загрузке VSPackage \(как правило, при вызове команды или открытии окна\) текст записывается в журнал действий.  
  
### Для просмотра журнала активности  
  
1.  Поиск данных в Visual Studio журналом во вложенной папке: *% AppData %*\\Microsoft\\VisualStudio\\14.0\\ActivityLog.XML...  
  
2.  Откройте журнал действий в любом текстовом редакторе. Ниже приведен типичный записи.  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## Отказоустойчивость  
 Поскольку журнал действий — это служба, журналом недоступен в конструкторе VSPackage.  
  
 Вы должны получить журнал действий непосредственно перед записью в него. Не кэшировать или сохранить журнал действий для использования в будущем.  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Устранение неполадок пакеты VSPackage](../extensibility/troubleshooting-vspackages.md)   
 [Пакеты VSPackage](../extensibility/internals/vspackages.md)