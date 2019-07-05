---
title: Декодируемый URI закодирован не | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fd8add72d016bc3f2e815f41c29c735505c8817
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006225"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Декодируемый URI закодирован неправильно
Предпринята попытка декодировать неправильно сформированное универсальный код (ресурса URI). Коды URI имеют специальный синтаксис; Большинство неалфавитных символов должны быть закодированы, прежде чем они могут использоваться в URI. Можно использовать `encodeURI` и `encodeURIComponent` методы для создания URI из обычной [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] строка.  
  
 Полный код URI состоит из последовательности компонентов и разделителей. Выглядит следующим образом:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Имена в угловых скобках представляют компоненты, а «:», «/», «;» и «?» являются зарезервированными символами, используемыми в качестве разделителей.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что вы пытаетесь расшифровать только допустимые URI. Не удается декодировать обычный [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] строк, они могут содержать недопустимые символы.  
  
## <a name="see-also"></a>См. также  
 [Функция decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Функция DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)