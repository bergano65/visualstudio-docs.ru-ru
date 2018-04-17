---
title: Отключение отладчика Visual Studio для Windows Workflow Foundation (для прежних версий) | Документы Microsoft
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: a609062f3f84538f7c1655cd5ca82971fc608f62
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Отключение отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)

В этом разделе описывается отключение [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] отладчика с помощью файла конфигурации, при построении [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] приложений в конструкторе рабочих процессов прежних версий Windows. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 По умолчанию отладчик [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] для [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] включен для ведущего процесса. Чтобы отключить отладку рабочего процесса, вы должны явно выключить ее путем добавления записи «DisableWorkflowDebugging»  **\<коммутаторы >** элемент в  **\<system.diagnostics >**раздел файла конфигурации узла.

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