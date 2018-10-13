---
title: Как отладить нарушения доступа при запуске программы без отладчика? | Документы Майкрософт
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
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 486b981311d93a93866622ccf80b6eabdee748ff
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290762"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Как отладить нарушения доступа при запуске программы без отладчика?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Описание проблемы  
 Программа прекрасно работает в среде Visual Studio, но при автономном запуске под операционной системой Windows возникает нарушение доступа. Как это отладить?  
  
## <a name="solution"></a>Решение  
 Задайте [Just-in-time отладки](../debugger/just-in-time-debugging-in-visual-studio.md) параметр и запустите автономное выполнение программы до момента возникновения нарушения доступа. Затем в **нарушение прав доступа** диалоговое окно, можно щелкнуть **отменить** для запуска отладчика.  
  
 Кроме того, обратитесь к статье Q133174 информационной базы данных, "How to Locate Where a General Protection (GP) Fault Occurs". Статьи базы знаний можно найти на компакт-диске библиотеки MSDN или поиска [ http://support.microsoft.com/ ](http://support.microsoft.com/).  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы отладки машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)



