---
title: Конструктор рабочих процессов - отключение отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 473ee507e35f5ec5df902df64ee34326dcf90a2b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969969"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Отключение отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)

В этом разделе описывается отключение отладчика Visual Studio, с помощью файла конфигурации, при построении приложений для Windows Workflow Foundation (WF) в конструкторе рабочих процессов прежних версий Windows. Используйте конструктор рабочих процессов прежних версий, для целевой платформы .NET Framework 3.5 или WinFX.

 По умолчанию Visual Studio отладчик для Windows Workflow Foundation (WF) включен для ведущего процесса. Чтобы отключить отладку рабочего процесса, вы должны явно выключить ее путем добавления записи «DisableWorkflowDebugging»  **\<коммутаторы >** элемент в  **\<system.diagnostics >** раздел файла конфигурации узла.

 В следующем примере показано, как изменить файл конфигурации главного узла, чтобы отключить отладку рабочего процесса.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>См. также

- [Вызов отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Отладка рабочих процессов прежних версий](../workflow-designer/debugging-legacy-workflows.md)