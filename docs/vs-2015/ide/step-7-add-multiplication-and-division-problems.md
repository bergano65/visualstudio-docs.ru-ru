---
title: Шаг 7. Добавление задач на умножение и деление | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 83c85dfdca66e9df3634f84795042b331bf3f760
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562490"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Шаг 7. Добавление задач на умножение и деление
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [шаг 7: Добавление умножение и деление](https://docs.microsoft.com/visualstudio/ide/step-7-add-multiplication-and-division-problems).  
  
В седьмой части этого учебника вам предстоит добавить задачи на умножение и деление. Сначала, однако, необходимо подумать, как внести это изменение. Рассмотрим начальный шаг, который предполагает сохранение значений.  
  
### <a name="to-add-multiplication-and-division-problems"></a>Добавление задач на умножение и деление  
  
1.  Добавьте в форму еще четыре целочисленные переменные.  
  
     [!code-csharp[VbExpressTutorial3Step7#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial3Step7#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#15)]  
  
2.  Как вы делали раньше, внесите изменения в метод `StartTheQuiz()`, чтобы он подставлял случайные числа для задач на умножение и деление.  
  
     [!code-csharp[VbExpressTutorial3Step7#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial3Step7#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#16)]  
  
3.  Измените метод `CheckTheAnswer()` таким образом, чтобы он также проверял задачи на умножение и деление.  
  
     [!code-csharp[VbExpressTutorial3Step7#17](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#17)]
     [!code-vb[VbExpressTutorial3Step7#17](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#17)]  
  
     Так как простого способа ввести знак умножения (×) и знак деления (÷) с клавиатуры нет, в языках Visual C# и Visual Basic используется знак звездочка (*) для умножения и знак косой черты (/) для деления.  
  
4.  Измените последнюю часть обработчика событий таймера Tick таким образом, чтобы по истечении времени этот обработчик событий проставлял правильный ответ.  
  
     [!code-csharp[VbExpressTutorial3Step7#23](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#23)]
     [!code-vb[VbExpressTutorial3Step7#23](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#23)]  
  
5.  Сохраните и выполните программу.  
  
     Игроки должны решить четыре задачи, чтобы пройти головоломку, как показано на следующем рисунке.  
  
     ![Математическая головоломка с четырьмя задачами](../ide/media/express-finishedquiz.png "Express_FinishedQuiz")  
Математическая головоломка с четырьмя задачами  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
-   Следующий шаг руководства см. в разделе [Step 8: Customize the Quiz](../ide/step-8-customize-the-quiz.md) (Шаг 8. Настройка головоломки).  
  
-   Предыдущий шаг руководства см. в разделе [Step 6: Add a Subtraction Problem](../ide/step-6-add-a-subtraction-problem.md) (Шаг 6. Добавление задачи на вычитание).



