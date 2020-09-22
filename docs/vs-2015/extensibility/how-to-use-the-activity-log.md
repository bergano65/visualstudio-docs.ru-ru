---
title: Как использовать журнал действий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d450e02d23159f186fd85bf1b687a2fb2c18e82a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843104"
---
# <a name="how-to-use-the-activity-log"></a>Практическое руководство. Использование журнала действий
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакеты VSPackage могут записывать сообщения в журнал действий. Эта функция особенно полезна для отладки пакетов VSPackage в розничных средах.  
  
> [!TIP]
> Журнал действий всегда включен. Visual Studio сохраняет последовательный буфер последних 100 записей, а также первые десять записей, имеющих общие сведения о конфигурации.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Запись записи в журнал действий  
  
1. Вставьте этот код в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод или в любой другой метод, кроме конструктора VSPackage:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Этот код получает <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> службу и приводит ее к <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейсу. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Записывает информационную запись в журнал действий, используя текущий контекст культуры.  
  
2. При загрузке VSPackage (обычно при вызове команды или открытии окна) текст записывается в журнал действий.  
  
### <a name="to-examine-the-activity-log"></a>Проверка журнала действий  
  
1. Найдите журнал действий во вложенной папке для данных Visual Studio: *% AppData%* \Microsoft\VisualStudio\14.0\ActivityLog.XML..  
  
2. Откройте журнал действий в любом текстовом редакторе. Вот типичная запись:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Так как журнал действий является службой, журнал действий недоступен в конструкторе VSPackage.  
  
 Журнал действий следует получить непосредственно перед записью в него. Не кэшировать или не сохраняйте журнал действий для будущего использования.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Устранение неполадок пакетов VSPackage](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
