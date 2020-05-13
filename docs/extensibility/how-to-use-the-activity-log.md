---
title: 'Как: Используйте журнал активности Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64986be303370cf8c9048612ff3d44e82e96805a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710585"
---
# <a name="how-to-use-the-activity-log"></a>Как: Использование журнала активности
VSPackages может записывать сообщения в журнал активности. Эта функция особенно полезна для отладки VSPackages в розничных средах.

> [!TIP]
> Регистрация активности всегда включена. Visual Studio сохраняет скользящийся буфер последних 100 записей, а также первые 10 записей, которые имеют общую информацию о конфигурации.

## <a name="to-write-an-entry-to-the-activity-log"></a>Запись записи в журнал активности

1. Вставьте этот <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> код в метод или в любой другой метод, кроме конструктора VSPackage:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Этот код <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> получает службу и <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> отбрасывает ее в интерфейс. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>записывает информационную запись в журнал активности с использованием текущего культурного контекста.

2. При загрузке VSPackage (обычно при вызове команды или открытии окна) текст записываются в журнал активности.

## <a name="to-examine-the-activity-log"></a>Изучить журнал активности

1. Запустите Visual Studio с переключателем командной строки [/Log](../ide/reference/log-devenv-exe.md) для записи ActivityLog.xml на диск во время сеанса.

2. После закрытия Visual Studio найдите журнал активности в подфолдере для данных Visual Studio:

   <em> *%AppData%</em>(версия Microsoft-VisualStudio\\\<>»ActivityLog.xml*.

3. Откройте журнал активности с помощью любого текстового редактора. Вот типичная запись:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Отказоустойчивость

Поскольку журнал активности является службой, журнал активности недоступен в конструкторе VSPackage.

Вы должны получить журнал активности непосредственно перед тем, как написать на него. Не кэшировать или сохранять журнал активности для использования в будущем.

## <a name="see-also"></a>См. также

- [/Лог (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Устранение неполадок, связанных с пакетами VSPackage](../extensibility/troubleshooting-vspackages.md)
- [Пакеты VSPackage](../extensibility/internals/vspackages.md)
