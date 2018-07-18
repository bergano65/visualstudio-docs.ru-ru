---
title: Отказано в доступе | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9c097cd09712d19acf5a0e4999b5c7a47469f958
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632734"
---
# <a name="access-is-denied"></a>Отказано в доступе
Скрипт попытался получить доступ к данным из источника, который не является узлом текущей страницы. Политика одного источника, которой следует Internet Explorer и другие браузеры, позволяет скриптам получать доступ к данным только из тех источников, которые находятся в той же схеме, на том же узле и в том же порте, что и URL-адрес текущей страницы.  
  
 Например, если открыта страница https://employees.mycompany.com, вы не сможете получить доступ к данным по следующим URL-адресам:  
  
-   http://data.contoso.com, поскольку вместо HTTPS здесь используется HTTP.  
  
-   https://somedatasource.com, поскольку это другой домен.  
  
-   https://employees.mycompany.com:8888, поскольку здесь используется другой порт.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Проверьте, поддерживает ли API, который вы пытаетесь вызвать, JSONP или CORS (два способа запроса данных, позволяющих создавать скрипты для безопасного обращения к другим доменам).  
  
-   Если вызывается API REST, переадресуйте этот вызов на код со стороны вашего сервера, а затем добавьте в скрипты на стороне клиента новую конечную точку REST.  
  
     Дополнительные сведения см. в документации по политике одного источника, JSONP и CORS.