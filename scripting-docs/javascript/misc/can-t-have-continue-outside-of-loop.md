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
ms.openlocfilehash: 804c23c45379a10d91c2888ac321c18f2067a1e4
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825695"
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
