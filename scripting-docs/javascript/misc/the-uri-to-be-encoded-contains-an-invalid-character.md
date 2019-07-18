---
title: Кодируемый URI содержит недопустимый символ | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: f2f9111acf656bf882a3d506fe95b8361f3693ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006212"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>Кодируемый URI содержит недопустимый символ
Была предпринята попытка кодирования строки как универсальный код ресурса (URI), но он содержит недопустимые символы. Несмотря на то, что большинство символы допустимы в строках, преобразуемых в URI, некоторые последовательности знаков Юникода не допускаются.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что Кодируемая строка содержит только допустимые последовательности Юникода. Полный код URI состоит из последовательности компонентов и разделителей. Имена в угловых скобках представляют компоненты, а «:», «/», «;» и «?» являются зарезервированными символами, используемыми в качестве разделителей. Выглядит следующим образом:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>См. также  
 [Функция encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Функция encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)