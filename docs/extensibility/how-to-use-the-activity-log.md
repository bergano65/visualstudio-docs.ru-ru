---
title: Практическое руководство. Использование журнала действий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d6aca6166486d0eda1a4a92167c0e8d6a8a2924
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63415531"
---
# <a name="how-to-use-the-activity-log"></a>Практическое руководство. Использование журнала действий
Пакеты VSPackage может записать события в журнале действий. Эта функция особенно полезна для отладки пакетов VSPackage в средах розничной торговли.

> [!TIP]
> Журнал действий всегда включен. Visual Studio будет хранить скользящий буфер последние 100 записей, а также первые 10 записей, которые имеют общие сведения о настройке.

## <a name="to-write-an-entry-to-the-activity-log"></a>Для записи в журнал действий

1. Вставьте этот код в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метода или в любой другой метод, кроме VSPackage конструктора:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Этот код получает <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> службы и приводит его к <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> интерфейс. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Записывает информационную запись в журнал действий с использованием текущего контекста культуры.

2. После загрузки VSPackage (как правило, при вызове команды или открытии окна) текст записывается в журнал действий.

## <a name="to-examine-the-activity-log"></a>Для просмотра журнала действий

1. Запустите Visual Studio с [/Log](../ide/reference/log-devenv-exe.md) параметр командной строки для записи ActivityLog.xml на диск во время сеанса.

2. После закрытия Visual Studio, найти журнал действий во вложенной папке для данных Visual Studio:

   <em>*%AppData%</em>\Microsoft\VisualStudio\\\<version>\ActivityLog.xml*.

3. Откройте журнал действий в любом текстовом редакторе. Ниже приведен типичный записи:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Отказоустойчивость

Так как журнал действий — это служба, журнал действий недоступна в конструкторе пакета VSPackage.

Журнал действий должен быть получен только перед записью в него. Не кэшировать и журнала действий для использования в будущем.

## <a name="see-also"></a>См. также

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Устранение неполадок, связанных с пакетами VSPackage](../extensibility/troubleshooting-vspackages.md)
- [Пакеты VSPackage](../extensibility/internals/vspackages.md)
