---
title: Декодируемый URI закодирован не | Документация Майкрософт
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
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d37ca55dfd701aaeba2af729511a5ae6a4fa5f4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841823"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Декодируемый URI закодирован неправильно
Предпринята попытка декодировать неправильно сформированное универсальный код (ресурса URI). Коды URI имеют специальный синтаксис; Большинство неалфавитных символов должны быть закодированы, прежде чем они могут использоваться в URI. Можно использовать `encodeURI` и `encodeURIComponent` методы для создания URI из обычной [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] строка.  
  
 Полный код URI состоит из последовательности компонентов и разделителей. Выглядит следующим образом:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Имена в угловых скобках представляют компоненты, а «:», «/», «;» и «?» являются зарезервированными символами, используемыми в качестве разделителей.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Убедитесь, что вы пытаетесь расшифровать только допустимые URI. Не удается декодировать обычный [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] строк, они могут содержать недопустимые символы.  
  
## <a name="see-also"></a>См. также  
 [Функция decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Функция DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)