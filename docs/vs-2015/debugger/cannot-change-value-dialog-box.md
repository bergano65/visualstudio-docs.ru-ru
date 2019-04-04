---
title: Невозможно изменить значение-диалоговое окно | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfe275411346e499312ba51c50a3a2ac3f4ed7d5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990830"
---
# <a name="cannot-change-value-dialog-box"></a>Не удается изменить значение - диалоговое окно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Error  
 `The value of this variable cannot be changed` &#124;`The name` *имя* `does not exist in the current context` &#124; *различные сообщения*  
  
 Это окно сообщения появляется при попытке поменять содержимое переменной на недопустимое значение в окне отладчика (окно "Видимые переменные", "Контрольные значения" или "Локальные переменные") или в диалоговом окне "Быстрая проверка". Например, данное окно сообщения отображается при попытке задать целочисленной переменной значение символьной строки.  
  
## <a name="solution"></a>Решение  
 Следует убедиться, что данные, вводимые в окне отладчика или диалоговом окне "Быстрая проверка", представляют собой допустимое значение для задаваемой переменной.  
  
## <a name="see-also"></a>См. также  
 [Выражения в отладчике](../debugger/expressions-in-the-debugger.md)
