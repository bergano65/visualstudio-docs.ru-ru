---
title: Разрешение неоднозначности-диалоговое окно | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 115c3dc86515f44d5b4be85b95e54ca62022efd1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303190"
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



