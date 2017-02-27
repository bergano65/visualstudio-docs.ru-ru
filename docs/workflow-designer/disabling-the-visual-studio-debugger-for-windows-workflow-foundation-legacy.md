---
title: "Отключение отладчика Visual Studio для Windows Workflow Foundation (для прежних версий) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "отладка рабочих процессов, отключение отладки"
  - "отладчик рабочих процессов, отключение"
  - "рабочие процессы, отключение отладки"
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Отключение отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)
В этом разделе описывается отключение отладчика [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с помощью файла конфигурации при построении приложений [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] в средстве [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] более ранней версии.[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 По умолчанию отладчик [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] для [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] включен для ведущего процесса.Чтобы отключить отладку рабочего процесса, необходимо явно выключить ее путем добавления элемента **\<switches\>** записи «DisableWorkflowDebugging» в раздел **\<system.diagnostics\>** файла конфигурации узла.  
  
 В следующем примере показано, как изменить файл конфигурации главного узла, чтобы отключить отладку рабочего процесса.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="DisableWorkflowDebugging" value="true"/>  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## См. также  
 [Вызов отладчика Visual Studio для Windows Workflow Foundation \(для прежних версий\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Отладка рабочих процессов прежних версий](../workflow-designer/debugging-legacy-workflows.md)