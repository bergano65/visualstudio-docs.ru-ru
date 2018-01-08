---
title: "Не удается изменить значение-диалоговое окно | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7a6b5cc2c1a5317009225d8e86fd497dc4367787
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2018
---
# <a name="cannot-change-value-dialog-box"></a>Не удается изменить значение - диалоговое окно
## <a name="error"></a>Error  
 `The value of this variable cannot be changed`&#124; `The name` *имя* `does not exist in the current context` &#124; *другие сообщения*  
  
 Это окно сообщения появляется при попытке поменять содержимое переменной на недопустимое значение в окне отладчика (окно "Видимые переменные", "Контрольные значения" или "Локальные переменные") или в диалоговом окне "Быстрая проверка". Например, данное окно сообщения отображается при попытке задать целочисленной переменной значение символьной строки.  
  
## <a name="solution"></a>Решение  
 Следует убедиться, что данные, вводимые в окне отладчика или диалоговом окне "Быстрая проверка", представляют собой допустимое значение для задаваемой переменной.  
  
## <a name="see-also"></a>См. также  
 [Выражения в отладчике](../debugger/expressions-in-the-debugger.md)