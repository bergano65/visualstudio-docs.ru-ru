---
title: "Декодируемый URI имеет недопустимую кодировку | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d37ca55dfd701aaeba2af729511a5ae6a4fa5f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Декодируемый URI закодирован неправильно
Предпринята попытка декодировать неправильно сформированное универсальный код (ресурса URI). Коды URI имеют особый синтаксис; Большинство неалфавитных символов должны быть закодированы, прежде чем их можно использовать в URI. Можно использовать `encodeURI` и `encodeURIComponent` методы для создания URI стандартной [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] строки.  
  
 Полный код URI состоит из последовательности компонентов и разделителей. Выглядит следующим образом:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Имена в угловых скобках представляют компоненты и «:», «/», «;» и «?», зарезервированные символы, используемые в качестве разделителей.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Убедитесь, что вы пытаетесь декодирования только допустимых URI. Не удается декодировать в обычном [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] строк, они могут содержать недопустимые символы.  
  
## <a name="see-also"></a>См. также  
 [Функция decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Функция DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)