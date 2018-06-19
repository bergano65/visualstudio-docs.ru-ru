---
title: Кодируемый URI содержит недопустимый символ | Документы Microsoft
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
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e93d145ea6b0991123c2a7c80f8acf54a83a264
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632934"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Кодируемый URI содержит недопустимый символ
Предпринята попытка кодирования строки как универсальный код ресурса (URI), но он содержит недопустимые символы. Несмотря на то, что большинство символов являются допустимыми в строках, преобразуемых в URI, некоторые последовательности знаков Юникода, недопустимы.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Убедитесь, что Кодируемая строка содержит только допустимые последовательности Юникода. Полный код URI состоит из последовательности компонентов и разделителей. Имена в угловых скобках представляют компоненты и «:», «/», «;» и «?», зарезервированные символы, используемые в качестве разделителей. Выглядит следующим образом:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>См. также  
 [Функция encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Функция encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)