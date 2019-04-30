---
title: «Continue» не может располагаться вне цикла | Документация Майкрософт
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 421cc23fb807a571b2b36f5f1def5df46a99492b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946619"
---
# <a name="cant-have-continue-outside-of-loop"></a>continue не может располагаться вне цикла
Вы попытались использовать **по-прежнему** инструкции вне цикла. **По-прежнему** инструкция может использоваться только в теле a:  
  
- `do-while` цикл,  
  
- `while` цикл,  
  
- **для** цикла  
  
- **/ в** цикла.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Убедитесь, что **по-прежнему** оператор находится внутри элементов управления:  
  
    - `do-while` цикл,  
  
    - `while` цикл,  
  
    - **для** цикла  
  
    - **/ в** цикла.  
  
## <a name="see-also"></a>См. также  
 [Оператор Continue](../../javascript/reference/continue-statement-javascript.md)   
 [Управление выполнением программы](../../javascript/controlling-program-flow-javascript.md)   
 [Устранение неполадок в скриптах](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)
