---
title: Параметр TargetCLR | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f8ea5bd3f1ec16f6deeae8365cc90541bc8b958
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2018
---
# <a name="targetclr"></a>TargetCLR
Параметр **TargetCLR** задает версию среды CLR для профилирования, если в приложении загружено несколько версий CLR.  
  
 По умолчанию Средства профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] обращаются к первой версии среды CLR, загруженной приложением.  
  
## <a name="syntax"></a>Синтаксис  
  
```cmd  
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
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /TargetCLR:v4.0.11003  
```