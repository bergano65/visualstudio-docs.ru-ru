---
title: 'Ошибка: Узел использует IP-адрес | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46eace1c566a2810c5914a49654f8393f425fdee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155754"
---
# <a name="error-site-uses-ip-address"></a>Ошибка: веб-узел использует IP-адрес
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта ошибка возникает, если в отладчике выполняется попытка автоматического присоединения к веб-приложению, которое использует IP-адрес. Это происходит при изменении в IIS параметра **идентификация веб-узла** на значение **определенный IP-адрес**.  
  
 Для работы автопривязки необходимо создать проект с определенным IP-адресом вместо имени компьютера. В противном случае имя машины будет заменено отладчиком на имя "localhost". Это вызовет сбой отправки команды службам IIS.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1. Используйте ручную привязку вместо автопривязки (в меню "Отладка" выберите пункт **Присоединение к процессу**).  
  
     —или—  
  
2. Измените параметр **Идентификация веб-узла IIS**.  
  
## <a name="see-also"></a>См. также  
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
