---
title: 'Ошибка: Веб-серверу не удалось найти запрошенный ресурс | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: f490006d21f51f48cd8b2d97da262015ab170f39
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808301"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Ошибка. Запрашиваемый ресурс не найден
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Службами IIS возвращена общая ошибка, связанная с безопасностью.  
  
 Одной из возможных причин является конфигурация безопасности сервера. В IIS версии 6.0 и более ранних версий использовался дополнительный компонент под названием URLScan, предназначенный для фильтрации подозрительных и неправильно сформированных запросов. В IIS версии 7.0 для этой же цели предусмотрена встроенная фильтрация запросов. В обоих случаях слишком строгие условия фильтрации запросов могут мешать Visual Studio производить отладку сервера.  
  
 Эта ошибка может быть вызвана многими причинами. К наиболее распространенным причинам относятся проблемы, связанные с установкой или конфигурацией IIS, конфигурацией веб-сайта или разрешениями в файловой системе. Можно попытаться получить доступ к ресурсу с помощью браузера. В зависимости от того, как настроены службы IIS, возможно, потребуется использовать локальный браузер на сервере или просмотреть журнал ошибок служб IIS, чтобы получить подробное сообщение об ошибке.  
  
 Дополнительные сведения об устранении неполадок IIS см. в разделе [управление и администрирование IIS](http://go.microsoft.com/fwlink/?LinkId=255872).  
  
## <a name="see-also"></a>См. также  
 [Средство безопасности UrlScan](http://www.microsoft.com/technet/security/tools/urlscan.mspx)   
 [Ошибка: веб-сервер заблокирован и блокирует команду DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)



