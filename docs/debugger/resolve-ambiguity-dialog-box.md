---
title: Диалоговое окно "Разрешение неоднозначности" | Документация Майкрософт
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
ms.openlocfilehash: 4257fd213d6401de381e25c74c126b8468b76057
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729845"
---
# <a name="resolve-ambiguity-dialog-box"></a>Разрешение неоднозначности - диалоговое окно
Диалоговое окно `Resolve Ambiguity` появляется, если отладчику не удалось выбрать расположение для отображения. Например, при использовании шаблонов C++ можно создавать несколько функций из одного шаблона функции. Если отладчик останавливается в некотором месте исходного кода в шаблоне и выбрана команда `Go To Disassembly`, отладчик оказывается перед выбором. Каждая функция, созданная из шаблона, имеет собственный дизассемблированный код, и отладчик не знает, какой именно код нужно отобразить. Диалоговое окно `Resolve Ambiguity` позволяет выбрать желаемое расположение из списка всех соответствующих расположений.

 `Choose the specific location` Перечисляются все расположения, соответствующие команде.

 `Address` Отображаются адреса памяти для каждой функции.

 `Function` Отображается имя каждой функции.

 `Module` Отображается модуль (EXE или DLL), содержащий объектный код для функции.

## <a name="see-also"></a>См. также
- [Выражения в отладчике](../debugger/expressions-in-the-debugger.md)