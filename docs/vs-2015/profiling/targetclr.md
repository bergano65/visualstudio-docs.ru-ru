---
title: Параметр TargetCLR | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9732480-287f-40f1-a4ff-b112e143b940
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e4691f2cdb138a034a9237e6b455c96c53f7ce7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220146"
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



