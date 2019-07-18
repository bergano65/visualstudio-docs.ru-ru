---
title: Параметр TargetCLR | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e4ca52f631b3e2de9c01daab7e6268c42f20268
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145611"
---
# <a name="targetclr"></a>TargetCLR
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметр **TargetCLR** задает версию среды CLR для профилирования, если в приложении загружено несколько версий CLR.  
  
 По умолчанию Средства профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] обращаются к первой версии среды CLR, загруженной приложением.  
  
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
