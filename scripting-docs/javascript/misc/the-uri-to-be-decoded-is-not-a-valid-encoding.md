---
title: URI для декодирования не является допустимой кодировкой | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 98d2ee08a52e86c435c58502da1ab4f68b594905
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816167"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>Декодируемый URI закодирован неправильно
Предпринята попытка декодировать URI с неправильным форматом (универсальный идентификатор ресурса). URI имеют специальный синтаксис; Большинство символов, отличных от буквенно-цифровых, должны быть закодированы, прежде чем их можно будет использовать в URI. `encodeURI` `encodeURIComponent` Для создания URI на основе обычной строки можно использовать методы и [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
 Полный URI состоит из последовательности компонентов и разделителей. Общая форма:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Имена в угловых скобках представляют компоненты, а ":", "/", ";" и "?" являются зарезервированными символами, используемыми в качестве разделителей.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что вы пытаетесь декодировать только допустимые URI. Нельзя декодировать обычные [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] строки, так как они могут содержать недопустимые символы.  
  
## <a name="see-also"></a>См. также  
 [Функция decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Функция decodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)