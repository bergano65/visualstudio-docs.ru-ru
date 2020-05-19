---
title: Использование окон отладчика при отладке активной программы | Документация Майкрософт
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 759d9a6a3beb55bf72a0f41a93cb26c8c15b0c5e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734057"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Как использовать окна отладчика при отладке активной программы?
## <a name="problem-description"></a>Описание проблемы
 Выполняются попытки отладить проблему отображения на экране. Для этого приходится держать программу активной, а это означает, что отсутствует доступ к окнам отладчика. Что можно сделать?

## <a name="solution"></a>Решение
 Если есть второй компьютер, используйте удаленную отладку. С двумя компьютерами можно посмотреть отображение на экране на удаленном компьютере, работая в отладчике на основном хосте. Дополнительные сведения об удаленной отладке см. в разделе [Удаленная отладка](../debugger/remote-debugging.md).

## <a name="see-also"></a>См. также
- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)