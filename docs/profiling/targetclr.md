---
title: "Параметр TargetCLR | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba512ba2004ec90c806e5e41d3c91c7bbb0587cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="targetclr"></a>TargetCLR
Параметр **TargetCLR** задает версию среды CLR для профилирования, если в приложении загружено несколько версий CLR.  
  
 По умолчанию Средства профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] обращаются к первой версии среды CLR, загруженной приложением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach:PID} /TargetCLR[:ClrVersion] [Options]   
```  
  
#### <a name="parameters"></a>Параметры  
 `ClrVersion`  
 Номер версии среды CLR. Используйте формат версии **vN.N.NNNNN**.  
  
## <a name="required-options"></a>Обязательные параметры  
 Параметр **TargetCLR** может использоваться только с параметрами **Launch** или **Attach**.  
  
 **Launch:** `AppName`  
 Запускает указанное приложение и начинает профилирование.  
  
 **Attach:** `PID`  
 Начинает профилирование указанного процесса.  
  
## <a name="example"></a>Пример  
 В этом примере параметр TargetCLR используется для обеспечения профилирования среды CLR версии 4.0.11003.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```