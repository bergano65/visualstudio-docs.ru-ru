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
ms.openlocfilehash: 2729f3d3cc0cd8a2411dcc9d999ba26100ba5aa2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-program"></a>Как сохранить фокусировку при пошаговом выполнении программы?
## <a name="description"></a>Описание  
 В программе возникает проблема, связанная с активацией окна. При пошаговом выполнении программы с отладчиком не удается воспроизвести проблему, так как программа теряет фокусировку. Есть ли способ избежать этого?  
  
## <a name="solution"></a>Решение  
 Если есть второй компьютер, используйте удаленную отладку. Можно управлять программой на удаленном компьютере, а на основном узле запустить отладчик. Дополнительные сведения см. в разделе [как: выберите удаленный компьютер](http://msdn.microsoft.com/en-us/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Присоединение к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)