---
title: Параметр User (VSPerfCmd) | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b390852c94477a6b02d43b0dbc7678384c622ced
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302007"
---
# <a name="user-vsperfcmd"></a>Параметр User (VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметр **User** указывает домен и имя пользователя учетной записи, которая является владельцем профилируемого процесса. Этот параметр является обязательным только в том случае, если процесс выполняется в качестве пользователя, отличного от пользователя, вошедшего в систему. Владелец процесса указан в столбце "Имя пользователя" на вкладке "Процессы" диспетчера задач Windows.  
  
 **Пользователя** параметр может быть указан только в командной строке, которая также содержит **запустить** параметром.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### <a name="parameters"></a>Параметры  
 `Domain`  
 Имя домена пользователя.  
  
 `UserName`  
 Имя пользователя.  
  
## <a name="required-options"></a>Обязательные параметры  
 Параметр **User** можно использовать только вместе с параметром **Start**.  
  
 **Start:** `Method`  
 Инициализирует профилировщик для заданного метода профилирования.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование параметра **User**.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## <a name="see-also"></a>См. также  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)



