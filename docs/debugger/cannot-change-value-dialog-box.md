---
title: Не удается изменить значение-диалоговое окно | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 23a6eb8059d9780e3b7343c6a7864896a0c529c6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31456693"
---
# <a name="cannot-change-value-dialog-box"></a>Не удается изменить значение - диалоговое окно
## <a name="error"></a>Error  
 `The value of this variable cannot be changed` &#124;`The name` *имя* `does not exist in the current context` &#124; *другие сообщения*  
  
 Это окно сообщения появляется при попытке поменять содержимое переменной на недопустимое значение в окне отладчика (окно "Видимые переменные", "Контрольные значения" или "Локальные переменные") или в диалоговом окне "Быстрая проверка". Например, данное окно сообщения отображается при попытке задать целочисленной переменной значение символьной строки.  
  
## <a name="solution"></a>Решение  
 Следует убедиться, что данные, вводимые в окне отладчика или диалоговом окне "Быстрая проверка", представляют собой допустимое значение для задаваемой переменной.  
  
## <a name="see-also"></a>См. также  
 [Выражения в отладчике](../debugger/expressions-in-the-debugger.md)