---
title: Разрешение неоднозначности-диалоговое окно | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.Disambig
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b35d305bbd011adc02692cd7c9c687ac0bfc7d45
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148791"
---
# <a name="resolve-ambiguity-dialog-box"></a>Разрешение неоднозначности - диалоговое окно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Диалоговое окно `Resolve Ambiguity` появляется, если отладчику не удалось выбрать расположение для отображения. Например, при использовании шаблонов C++ можно создавать несколько функций из одного шаблона функции. Если отладчик останавливается в некотором месте исходного кода в шаблоне и выбрана команда `Go To Disassembly`, отладчик оказывается перед выбором. Каждая функция, созданная из шаблона, имеет собственный дизассемблированный код, и отладчик не знает, какой именно код нужно отобразить. Диалоговое окно `Resolve Ambiguity` позволяет выбрать желаемое расположение из списка всех соответствующих расположений.  
  
 `Choose the specific location`  
 Перечисляются все расположения, соответствующие команде.  
  
 `Address`  
 Показываются адреса памяти для каждой функции.  
  
 `Function`  
 Отображается имя каждой функции.  
  
 `Module`  
 Отображается модуль (EXE или DLL), содержащий объектный код для функции.  
  
## <a name="see-also"></a>См. также  
 [Выражения в отладчике](../debugger/expressions-in-the-debugger.md)
