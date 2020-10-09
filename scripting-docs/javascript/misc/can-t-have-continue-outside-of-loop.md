---
title: "\"Continue\" не может находиться вне цикла | Документация Майкрософт"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d2d95259-b2bc-4069-9876-60c30ad600a3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14745c5789fe6c0350f83e46ee0e918f92789d96
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861979"
---
# <a name="cant-have-continue-outside-of-loop"></a>continue не может располагаться вне цикла
Предпринята попытка использовать инструкцию **Continue** за пределами цикла. Оператор **Continue** можно использовать только в теле:  
  
- `do-while` повторить  
  
- `while` повторить  
  
- цикл **for** ,  
  
- цикл **for/in** .  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что оператор **Continue** присутствует в теле:  
  
  - `do-while` повторить  

  - `while` повторить  

  - цикл **for** ,  

  - цикл **for/in** .  
  
## <a name="see-also"></a>См. также  
 [Оператор Continue](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/continue)   
 [Управление ходом выполнения программы](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Устранение неполадок в скриптах](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)