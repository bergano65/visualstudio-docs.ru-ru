---
title: Разрешение неоднозначности-диалоговое окно | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.Disambig
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2cad82add5d397991f2c3e7532bbbf2559f9819e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033076"
---
# <a name="resolve-ambiguity-dialog-box"></a>Разрешение неоднозначности - диалоговое окно
Диалоговое окно `Resolve Ambiguity` появляется, если отладчику не удалось выбрать расположение для отображения. Например, при использовании шаблонов C++ можно создавать несколько функций из одного шаблона функции. Если отладчик останавливается в некотором месте исходного кода в шаблоне и выбрана команда `Go To Disassembly`, отладчик оказывается перед выбором. Каждая функция, созданная из шаблона, имеет собственный дизассемблированный код, и отладчик не знает, какой именно код нужно отобразить. Диалоговое окно `Resolve Ambiguity` позволяет выбрать желаемое расположение из списка всех соответствующих расположений.  
  
 `Choose the specific location`  
 Перечисляются все расположения, соответствующие команде.  
  
 `Address`  
 Показываются адреса памяти для каждой функции.  
  
 `Function`  
 Отображается имя каждой функции.  
  
 `Module`  
 Отображается модуль (EXE или DLL), содержащий объектный код для функции.  
  
## <a name="see-also"></a>См. также раздел  
 [Выражения в отладчике](../debugger/expressions-in-the-debugger.md)