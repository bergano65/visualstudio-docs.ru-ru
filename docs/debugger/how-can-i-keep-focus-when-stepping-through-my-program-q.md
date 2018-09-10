---
title: Как сохранить фокусировку при пошаговом выполнении программы? | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.stepping
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], stepping
- focus, keeping
- stepping, focus
- windows, troubleshooting activation
ms.assetid: 11a30580-3a1a-4be8-a241-0abdc758302e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 509e169c7ede0d96882fa2c97eaf7b2c6eb78afb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280913"
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-program"></a>Как сохранить фокусировку при пошаговом выполнении программы?
## <a name="description"></a>Описание  
 В программе возникает проблема, связанная с активацией окна. При пошаговом выполнении программы с отладчиком не удается воспроизвести проблему, так как программа теряет фокусировку. Есть ли способ избежать этого?  
  
## <a name="solution"></a>Решение  
 Если есть второй компьютер, используйте удаленную отладку. Можно управлять программой на удаленном компьютере, а на основном узле запустить отладчик. Дополнительные сведения см. в разделе [как: выберите удаленный компьютер](/previous-versions/visualstudio/visual-studio-2010/w8wtw2f3(v=vs.100)).  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы отладки машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Присоединение к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)