---
title: 'Ошибка: Узел использует IP-адрес | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b726902c57cc95b694f2ab7e656a444ed42a0ba9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470908"
---
# <a name="error-site-uses-ip-address"></a>Ошибка: веб-узел использует IP-адрес
Эта ошибка возникает, если в отладчике выполняется попытка автоматического присоединения к веб-приложению, которое использует IP-адрес. Это происходит при изменении **Идентификация веб-узла** для **определенный IP-адрес** в службах IIS.  
  
 Для работы автопривязки необходимо создать проект с определенным IP-адресом вместо имени компьютера. В противном случае имя машины будет заменено отладчиком на имя "localhost". Это вызовет сбой отправки команды службам IIS.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Используйте ручную привязку вместо автопривязки (в меню "Отладка" выберите **присоединиться к процессу**).  
  
     —или—  
  
2.  Изменение **идентификация IIS веб-узла** параметр.  
  
## <a name="see-also"></a>См. также  
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)