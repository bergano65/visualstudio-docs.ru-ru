---
title: Сохранение фокусировки при пошаговом выполнении приложения | Документация Майкрософт
Description: При отладке проблем с активацией окна используйте удаленную отладку, чтобы фокус оставался на программе.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b821c374a87983ab8cb2667b434b1509e8449f31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911443"
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-app"></a>Как сохранить фокусировку при пошаговом выполнении приложения?
## <a name="description"></a>Описание
 В программе возникает проблема, связанная с активацией окна. При пошаговом выполнении программы с отладчиком не удается воспроизвести проблему, так как программа теряет фокусировку. Есть ли способ избежать этого?

## <a name="solution"></a>Решение
 Если есть второй компьютер, используйте удаленную отладку. Можно управлять программой на удаленном компьютере, а на основном хосте запустить отладчик. Дополнительные сведения см. в разделе [Практическое руководство. выбрать удаленный компьютер](/previous-versions/visualstudio/visual-studio-2010/w8wtw2f3(v=vs.100)).

## <a name="see-also"></a>См. также
- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Подключение к выполняющимся процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)