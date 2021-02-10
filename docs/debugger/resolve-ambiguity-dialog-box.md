---
title: Диалоговое окно "Разрешение неоднозначности" | Документация Майкрософт
description: Сведения о диалоговом окне "Разрешение неоднозначности" в Visual Studio, которое появляется, когда отладчику не удается выбрать расположение для отображения.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ee7b83630935b948d29150763e0ad5b9c435175f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891323"
---
# <a name="resolve-ambiguity-dialog-box"></a>Разрешение неоднозначности - диалоговое окно
Диалоговое окно `Resolve Ambiguity` появляется, если отладчику не удалось выбрать расположение для отображения. Например, при использовании шаблонов C++ можно создавать несколько функций из одного шаблона функции. Если отладчик останавливается в некотором месте исходного кода в шаблоне и выбрана команда `Go To Disassembly`, отладчик оказывается перед выбором. Каждая функция, созданная из шаблона, имеет собственный дизассемблированный код, и отладчик не знает, какой именно код нужно отобразить. Диалоговое окно `Resolve Ambiguity` позволяет выбрать желаемое расположение из списка всех соответствующих расположений.

 `Choose the specific location` Перечисляются все расположения, соответствующие команде.

 `Address` Отображаются адреса памяти для каждой функции.

 `Function` Отображается имя каждой функции.

 `Module` Отображается модуль (EXE или DLL), содержащий объектный код для функции.

## <a name="see-also"></a>См. также
- [Выражения в отладчике](../debugger/expressions-in-the-debugger.md)