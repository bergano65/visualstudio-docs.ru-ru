---
title: 'Ошибка: веб-сервер не обнаружил запрашиваемый ресурс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 555bb56ee84b7bc48f6b6453c11daef366f97e49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845121"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Ошибка: веб-сервер не обнаружил запрашиваемый ресурс
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Службами IIS возвращена общая ошибка, связанная с безопасностью.  
  
 Одной из возможных причин является конфигурация безопасности сервера. В IIS версии 6.0 и более ранних версий использовался дополнительный компонент под названием URLScan, предназначенный для фильтрации подозрительных и неправильно сформированных запросов. В IIS версии 7.0 для этой же цели предусмотрена встроенная фильтрация запросов. В обоих случаях слишком строгие условия фильтрации запросов могут мешать Visual Studio производить отладку сервера.  
  
 Эта ошибка может быть вызвана многими причинами. К наиболее распространенным причинам относятся проблемы, связанные с установкой или конфигурацией IIS, конфигурацией веб-сайта или разрешениями в файловой системе. Можно попытаться получить доступ к ресурсу с помощью браузера. В зависимости от того, как настроены службы IIS, возможно, потребуется использовать локальный браузер на сервере или просмотреть журнал ошибок служб IIS, чтобы получить подробное сообщение об ошибке.  
  
 Дополнительные сведения об устранении неполадок IIS см. в разделе [Управление и администрирование IIS](https://www.iis.net/learn/manage/provisioning-and-managing-iis/iis-management-and-administration).  
  
## <a name="see-also"></a>См. также:  
 [Средство защиты UrlScan](/iis/extensions/working-with-urlscan/urlscan-3-reference)   
 [Ошибка: веб-сервер заблокирован и блокирует команду DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
