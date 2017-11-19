---
title: "Ошибка: Веб-сервере не удалось найти запрошенный ресурс | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 782abbf8a5cb30801bbe6041143e031792ff247a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Ошибка. Запрашиваемый ресурс не найден
Службами IIS возвращена общая ошибка, связанная с безопасностью.  
  
 Одной из возможных причин является конфигурация безопасности сервера. В IIS версии 6.0 и более ранних версий использовался дополнительный компонент под названием URLScan, предназначенный для фильтрации подозрительных и неправильно сформированных запросов. В IIS версии 7.0 для этой же цели предусмотрена встроенная фильтрация запросов. В обоих случаях слишком строгие условия фильтрации запросов могут мешать Visual Studio производить отладку сервера.  
  
 Эта ошибка может быть вызвана многими причинами. К наиболее распространенным причинам относятся проблемы, связанные с установкой или конфигурацией IIS, конфигурацией веб-сайта или разрешениями в файловой системе. Можно попытаться получить доступ к ресурсу с помощью браузера. В зависимости от того, как настроены службы IIS, возможно, потребуется использовать локальный браузер на сервере или просмотреть журнал ошибок служб IIS, чтобы получить подробное сообщение об ошибке.  
  
 Дополнительные сведения об устранении неполадок в службах IIS см. в разделе [управления IIS и администрирования](http://go.microsoft.com/fwlink/?LinkId=255872).  
  
## <a name="see-also"></a>См. также  
 [Средство безопасности UrlScan](http://www.microsoft.com/technet/security/tools/urlscan.mspx)   
 [Ошибка: веб-сервер заблокирован и блокирует команду DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)