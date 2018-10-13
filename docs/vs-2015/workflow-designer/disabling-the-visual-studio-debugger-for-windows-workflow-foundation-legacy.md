---
title: Отключение отладчика Visual Studio для Windows Workflow Foundation (для прежних версий) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: fab5278c5f0c7385dd767b8994a04124bc40b283
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172215"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Отключение отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)
В этом разделе описывается отключение отладчика [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] с помощью файла конфигурации при построении приложений [!INCLUDE[wf](../includes/wf-md.md)] в средстве [!INCLUDE[wfd1](../includes/wfd1-md.md)] более ранней версии. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 По умолчанию отладчик [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] для [!INCLUDE[wf](../includes/wf-md.md)] включен для ведущего процесса. Чтобы отключить отладку рабочего процесса, вам необходимо явно выключить ее путем добавления записи «DisableWorkflowDebugging»  **\<коммутаторы >** элемент в  **\<system.diagnostics >** раздел файла конфигурации узла.  
  
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
  
## <a name="see-also"></a>См. также  
 [Вызов отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Отладка рабочих процессов прежних версий](../workflow-designer/debugging-legacy-workflows.md)