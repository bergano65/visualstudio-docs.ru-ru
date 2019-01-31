---
title: 'Ошибка: Веб-сервер заблокирован и блокирует команду DEBUG | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_debug_verb_blocked
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 277619cb89003aea9dca58678f251f2f21826046
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026597"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Ошибка: веб-сервер заблокирован и блокирует команду DEBUG
Сбой пошаговой отладки веб-приложения или веб-службы XML возникает, если запущено средство блокировки IIS при установленном и работающем приложении URLScan. В этом случае для IIS блокируется получение команды DEBUG.  
  
 URLScan — средство безопасности, работающее вместе со средством блокировки IIS, которое дает администраторам веб-узелов IIS возможность отключения ненужных возможностей, а также возможность ограничения обрабатываемых сервером типов HTTP-запросов. Блокируя определенные HTTP-запросы, средство безопасности URLScan предотвращает достижение сервера потенциально вредоносными запросами.  
  
 Если приложение выполняется в операционной системе Windows Server 2003 на IIS 6.0, то нет необходимости использовать средство блокировки IIS, поскольку IIS 6.0 обеспечивает такую функцию.  
  
### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>Разрешение отладки на веб-сервере с установленным средством URLScan  
  
1.  Найдите файл Urlscan.ini. Как правило, этот файл находится в каталоге:  
  
     C:\WINNT\System32\Inetsrv\urlscan  
  
2.  Создайте копию этого файла и присвойте этому файлу имя **Urlscan.old**.  
  
3.  Откройте исходную копию файла Urlscan.ini в блокноте или любом другом текстовом редакторе.  
  
4.  В файле Urlscan.ini найдите раздел [AllowVerbs]. Добавьте команду DEBUG в раздел [AllowVerbs]. Если в разделе [AllowVerbs] присутствует текст ";DEBUG", можно удалить точку с запятой, чтобы снять комментирование с этой команды.  
  
5.  Найдите раздел [DenyVerbs]. Если команда DEBUG присутствует в разделе [DenyVerbs], ее необходимо удалить.  
  
6.  Сохраните файл.  
  
7.  Перезагрузите сервер или перезапустите IIS.  
  
## <a name="see-also"></a>См. также раздел  
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Ошибка: запрашиваемый ресурс не найден](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)