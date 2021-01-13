---
title: Диалоговое окно "Не удается изменить значение" | Документация Майкрософт
description: Ознакомьтесь с диалоговым окном "Не удается изменить значение", которое появляется в Visual Studio, при попытке изменения значения переменной на недопустимое в окне отладчика или QuickWatch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf4181d7ff56bd1a5cf3f195bcea5b02aa023629
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729058"
---
# <a name="cannot-change-value-dialog-box"></a>Не удается изменить значение - диалоговое окно
## <a name="error"></a>Ошибка
 `The value of this variable cannot be changed` &#124; `The name` *имя* `does not exist in the current context` &#124; *различные иные сообщения*

 Это окно сообщения появляется при попытке поменять содержимое переменной на недопустимое значение в окне отладчика (окно "Видимые переменные", "Контрольные значения" или "Локальные переменные") или в диалоговом окне "Быстрая проверка". Например, данное окно сообщения отображается при попытке задать целочисленной переменной значение символьной строки.

## <a name="solution"></a>Решение
 Следует убедиться, что данные, вводимые в окне отладчика или диалоговом окне "Быстрая проверка", представляют собой допустимое значение для задаваемой переменной.

## <a name="see-also"></a>См. также

- [Выражения в отладчике](../debugger/expressions-in-the-debugger.md)