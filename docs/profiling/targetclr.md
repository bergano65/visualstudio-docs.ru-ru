---
title: "TargetCLR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# TargetCLR
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Параметр **TargetCLR** задает версию среды CLR для профилирования, если в приложении загружено несколько версий CLR.  
  
 По умолчанию средства профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] обращаются к первой версии CLR, загруженной приложением.  
  
## Синтаксис  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### Параметры  
 `ClrVersion`  
 Номер версии CLR.  Используйте формат версии **vN.N.NNNNN**.  
  
## Обязательные параметры  
 Параметр **TargetCLR** может использоваться только с параметрами **Launch** или **Attach**.  
  
 **Launch:** `AppName`  
 Запускает заданное приложение и начинает профилирование.  
  
 **Attach:** `PID`  
 Начинает профилирование заданного процесса.  
  
## Пример  
 В данном примере параметр TargetCLR используется для обеспечения профилирования среды CLR версии 4.0.11003.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```