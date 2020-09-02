---
title: URI для кодирования содержит недопустимый символ | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6091968dcbdd98240b1705e0fa7dc855dad3bda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816076"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Кодируемый URI содержит недопустимый символ
Предпринята попытка кодирования строки в виде универсального кода ресурса (URI), но она содержала недопустимые символы. Хотя большинство символов допустимо в строках для преобразования в URI, некоторые последовательности символов Юникода являются недопустимыми.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что строка, которая должна быть закодирована, содержит только допустимые последовательности Юникода. Полный URI состоит из последовательности компонентов и разделителей. Имена в угловых скобках представляют компоненты, а ":", "/", ";" и "?" являются зарезервированными символами, используемыми в качестве разделителей. Общая форма:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>См. также раздел  
 [Функция encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Функция encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)