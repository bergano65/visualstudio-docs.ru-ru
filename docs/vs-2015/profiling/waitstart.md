---
title: WaitStart | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c737177-2dfb-4150-963e-a49ac9aaa591
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13f52c2c9449b8f1abdc51fca9c9f989163a2a39
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760292"
---
# <a name="waitstart"></a>WaitStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Благодаря параметру WaitStart подкоманда VSPerfCmd.exe Start возвращается только после инициализации профилировщика или через указанное число секунд. По умолчанию команда Start возвращается немедленно. Если подкоманда Start возвращается без инициализации профилировщика, возвращается ошибка. Если не указано число секунд, команда Start ожидает неограниченное время.  
  
 Параметр WaitStart полезно использовать в пакетных файлах, чтобы обеспечивать инициализацию профилировщика.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName[Options] /StartWait[:Seconds]  
```  
  
#### <a name="parameters"></a>Параметры  
 `Seconds`  
 Число секунд ожидания перед возвращением подкоманды Start.  
  
## <a name="required-options"></a>Обязательные параметры  
 Параметр WaitStart может использоваться только с подкомандой Start.  
  
 **Output:** `filename`  
 Задает имя выходного файла.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В этом примере пакетного файла команда Start ожидает инициализацию профилировщика 5 секунд.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WaitStart:5  
if not %errorlevel% 0 goto :error_tag  
VSPerfCmd.exe /Launch:TestApp.exe  
goto :end  
:error_tag  
@echo Could not start Profiler!  
@echo Error %errorlevel%  
:end  
```



