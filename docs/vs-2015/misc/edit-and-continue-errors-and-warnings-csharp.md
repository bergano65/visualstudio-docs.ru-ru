---
title: Ошибки и предупреждения для изменения и продолженияC#() | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.csharp.enc.error_4001
- vs.csharp.enc.error_4034
- vs.csharp.enc.error_4003
- vs.csharp.enc.error_4026
- vs.csharp.enc.error_4032
- vs.csharp.enc.error_4017
- vs.csharp.enc.error_4053
- vs.csharp.enc.error_4024
- vs.csharp.enc.error_4012
- vs.csharp.enc.error_4066
- vs.csharp.enc.error_4020
- vs.csharp.enc.error_4008
- vs.csharp.enc.error_4033
- vs.csharp.enc.error_4014
- vs.csharp.enc.error_4023
- vs.csharp.enc.error_4011
- vs.csharp.enc.error_4006
- vs.csharp.enc.error_4059
- vs.csharp.enc.error_4015
- vs.csharp.enc.error_4018
- vs.csharp.enc.error_4028
- vs.csharp.enc.error_4013
- vs.csharp.enc.error_4009
- vs.csharp.enc.error_4021
- vs.csharp.enc.error_4065
- vs.csharp.enc.error_4029
- vs.csharp.enc.error_4058
- vs.csharp.enc.error_4019
- vs.csharp.enc.error_4007
- vs.csharp.enc.error_4052
- vs.csharp.enc.error_4025
- vs.csharp.enc.error_4055
- vs.csharp.enc.error_4022
- vs.csharp.enc.error_4002
- vs.csharp.enc.error_4016
- vs.csharp.enc.error_4043
- vs.csharp.enc.error_4027
- vs.csharp.enc.error_4054
- vs.csharp.enc.error_4004
- vs.csharp.enc.error_4010
- vs.csharp.enc.error_4030
- vs.csharp.enc.error_4005
- vs.csharp.enc.error_4035
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], errors and warnings
- errors [C#], debugging
- errors [debugger], Edit and Continue
ms.assetid: c0e12b0a-8009-4a4a-979f-c804a91a5d9b
caps.latest.revision: 11
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eec40bc584e831f8b43b79c9bc7cee5a48a291aa
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850976"
---
# <a name="edit-and-continue-errors-and-warnings-c"></a>Ошибки и предупреждения режима "Изменить и продолжить" (C#)
Были внесены изменения в раздел кода, изменение которого не допускается при использовании операции "Изменить и продолжить" языка Visual C#.  
  
 Операция "Изменить и продолжить" в [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)] позволяет остановить выполнение программы в режиме приостановки выполнения, внести изменения в исполняемый код, а затем возобновить выполнение программы с учетом внесенных изменений.  
  
 Изменения в объявляющем коде, меняющие общедоступную (public) структуру класса, в общем случае запрещены. Кроме того, не разрешены некоторые виды изменений в теле метода или свойства, а также в объявлениях со спецификатором доступа private в пределах класса. Операция "Изменить и продолжить" по возможности помечает запрещенный к изменению код светло-серым и отображает сообщение об ошибке.  
  
 Дополнительные сведения об изменениях, поддерживаемых операцией "Изменить и продолжить" для [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], см. в разделе [Supported Code Changes (C#)](../debugger/supported-code-changes-csharp.md). Если требуются дополнительные сведения о конкретной ошибке или предупреждении, можно поискать ответ или разместить вопрос на [форуме по IDE Visual C#](https://social.msdn.microsoft.com/Forums/en-US/csharpide/threads)на веб-сайте MSDN.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1. Выберите команду **Отменить** в меню **Отладка** для отмены изменений.  
  
     \- или -  
  
2. Остановите сеанс отладки, внесите изменения и начните новый сеанс отладки.  
  
## <a name="see-also"></a>См. также раздел  
 [Режим "Изменить и продолжить" (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
