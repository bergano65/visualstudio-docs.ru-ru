---
title: "Сопоставление методов в стеке вызовов при отладке в Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 39
author: mikejo5000
ms.author: mikejo
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ab08446140608a65b6894b3015c52227040611fd
ms.lasthandoff: 02/22/2017

---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Сопоставление методов в визуализации стека вызовов при отладке в Visual Studio
Для визуального отслеживания стека вызовов при отладке можно создать карту кода. В это сопоставление можно вносить примечания для отслеживания операций, выполняемых кодом. Таким образом, вы сможете сосредоточиться на поиске ошибок.  
  
 ![Отладка со стеками вызовов на картах кода](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")  
  
 Требуется:  
  
-   [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   Код, поддерживающий отладку: Visual C# .NET, Visual Basic .NET, C++, JavaScript и X++  
  
 См.: [видео: визуальная отладка с интеграцией отладчика сопоставления кода (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418) • [стек вызовов](#MapStack) • [сделать примечаний к коду](#MakeNotes) • [обновление сопоставления путем добавления следующего стека вызовов](#UpdateMap) • [Добавление связанного кода в сопоставление](#AddRelatedCode) • [поиск ошибок с помощью сопоставления](#FindBugs) • [A & вопрос:](#QA)  
  
 Сведения о командах и действиях, которые можно использовать при работе с картами кода см. в разделе [Просмотр и реорганизация карт кода](../modeling/browse-and-rearrange-code-maps.md).  
  
##  <a name="a-namemapstacka-map-the-call-stack"></a><a name="MapStack"></a>Сопоставление стека вызова  
  
1.  Приступите к отладке. (Клавиатура: **F5**)  
  
2.  При переходе приложения в режиме приостановки выполнения или шаг с заходом в функцию выберите **карта кода**. (Keyboard: **Ctrl** + **Shift** + **`**)  
  
     ![Выберите код карты, чтобы запустить сопоставление стека вызовов](../debugger/media/debuggermap_choosecodemap.png "DebuggerMap_ChooseCodeMap")  
  
     Текущий стек вызовов выделен в новой карте кода оранжевым цветом:  
  
     ![В разделе стек вызовов на карте кода](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")  
  
     Эта карта будет автоматически обновляться в ходе отладки. В разделе [обновление сопоставления путем добавления следующего стека вызовов](#UpdateMap).  
  
##  <a name="a-namemakenotesa-make-notes-about-the-code"></a><a name="MakeNotes"></a>Добавление примечаний к коду  
 Добавьте комментарии для отслеживания операций, выполняемых в коде. Чтобы добавить новую строку в комментарий, нажмите клавишу **Shift + Return**.  
  
 ![Добавление комментария к стеку вызовов на карте кода](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")  
  
##  <a name="a-nameupdatemapa-update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a>Обновление сопоставления путем добавления следующего стека вызовов  
 Выполните приложение до следующей точки останова или зайдите в функцию. В сопоставление будет добавлен новый стек вызовов.  
  
 ![Обновление карты кода следующим стеком вызовов](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")  
  
##  <a name="a-nameaddrelatedcodea-add-related-code-to-the-map"></a><a name="AddRelatedCode"></a>Добавление связанного кода карты  
 Итак, сопоставление готово. Что дальше? При работе с Visual C#, .NET или Visual Basic .NET добавьте в него элементы, такие как поля, свойства и методы, для отслеживания операций в коде.  
  
 Дважды щелкните метод для просмотра его определения кода или используйте контекстное меню метода. (Клавиатура: выделите метод в сопоставлении и нажмите клавишу **F12**)  
  
 ![Перейти к определению кода метода на карте кода](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")  
  
 Добавьте элементы, которые необходимо отслеживать в сопоставлении.  
  
 ![Отображение полей в методе на карте кода со стеком вызовов](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")  
  
> [!NOTE]
>  По умолчанию при добавлении элементов в сопоставление также добавляются узлы родительской группы, соответствующие, например, классу, пространству имен или сборке. Хотя эта возможность полезна, можно сохранять карты простой, отключение этой функции с помощью **включить родительские элементы** кнопки на панели инструментов карты или нажав **CTRL** при добавлении элементов.  
  
 ![Поля, связанные с методом на карте кода со стеком вызовов](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")  
  
 Нетрудно определить, какие методы используют одинаковые поля. Последние добавленные элементы отображаются зеленым цветом.  
  
 Продолжайте формировать сопоставление, чтобы увидеть дополнительный код.  
  
 ![В разделе методы, использующие поле: карта кода со стеком вызовов](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")  
  
 ![Методы, использующие поле на карте кода со стеком вызовов](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")  
  
##  <a name="a-namefindbugsa-find-bugs-using-the-map"></a><a name="FindBugs"></a>Поиск ошибок с помощью карты  
 Визуализация кода поможет вам быстрее находить ошибки. Например, предположим, что вы ищите ошибку в программе для рисования. Когда вы создаете линию и пробуете отменить ее создание, ничего не происходит до тех пор, пока не будет нарисована следующая линия.  
  
 Установив точки останова в методах `clear`, `undo` и `Repaint`, вы начинаете отладку и создаете сопоставление, аналогичное представленному ниже:  
  
 ![Добавление другого стека вызовов на карту кода](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")  
  
 Учтите, что все жесты пользователя в сопоставлении вызывают метод `Repaint`, за исключением `undo`. Возможно, именно поэтому функция `undo` срабатывает не сразу.  
  
 Когда вы исправите ошибку и продолжите выполнение программы, в сопоставление будет добавлен новый вызов из `undo` в `Repaint`.  
  
 ![Добавление нового вызова метода в стек вызовов на карте кода](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")  
  
##  <a name="a-nameqaa-q--a"></a><a name="QA"></a> Вопросы и ответы  
  
-   **Не все вызовы отображаются на карте. Почему?**  
  
     По умолчанию в сопоставлении отображается только ваш код. Чтобы просмотреть внешний код, включите его в **стек вызовов** окна:  
  
     ![Отображение внешнего кода с помощью окна стека вызовов](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")  
  
     или отключите **включить только мой код** в параметрах отладки Visual Studio:  
  
     ![Показать внешний код, с помощью диалогового окна параметров](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")  
  
-   **Изменение сопоставления влияет на код?**  
  
     Изменение сопоставления никак не влияет на код. Можно свободно переименовать, изменить или удалить любой элемент в сопоставлении.  
  
-   **Что означает сообщение: «схема может основываться на устаревшего кода»?**  
  
     С момента последнего обновления сопоставления код мог измениться. Например, вызов в сопоставлении может уже не существовать в коде. Закройте сообщение, а затем попытайтесь повторить сборку решения, прежде чем повторно обновлять сопоставление.  
  
-   **Как управлять макетом сопоставления?**  
  
     Откройте **макета** меню на панели инструментов карты:  
  
    -   Измените макет по умолчанию.  
  
    -   Чтобы остановить автоматическую перекомпоновку сопоставления, отключите **автоматически формировать макет при отладке**.  
  
    -   Чтобы макет карты как можно реже, при добавлении элементов, отключите **последовательный макет**.  
  
-   **Можно использовать схему с другими пользователями?**  
  
     Сопоставление можно экспортировать, отправить его другим пользователям при наличии Microsoft Outlook или сохранить его в решении, чтобы можно было вернуть его в систему управления версиями Team Foundation.  
  
     ![Предоставление карте кода стек вызовов с другими](../debugger/media/debuggermap_sharewithothers.png "DebuggerMap_ShareWithOthers")  
  
-   **Остановка карты автоматически добавлять новые стеки вызова**  
  
     Выберите ![кнопка - отображение стека вызовов на код сопоставления автоматически](../debugger/media/debuggermap_automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") на панели инструментов карты. Чтобы вручную добавить текущий стек вызовов на карту, нажмите клавишу **Ctrl** + **Shift** + **`**.  
  
     Существующие стеки вызовов по-прежнему будут выделяться на сопоставлении во время отладки.  
  
-   **Что значки элементов и стрелки означают?**  
  
     Чтобы узнать дополнительные сведения об элементе, наведите на него указатель мыши и прочитайте подсказку. Можно также ознакомиться с **условных обозначений** чтобы узнать, что означает каждый значок.  
  
     ![Что означают значки на карте кода со стеком вызовов ] (../debugger/media/debuggermap_showlegend.png "DebuggerMap_ShowLegend")  
  
 См.: [стек вызовов](#MapStack) • [сделать примечаний к коду](#MakeNotes) • [обновление сопоставления путем добавления следующего стека вызовов](#UpdateMap) • [Добавление связанного кода в сопоставление](#AddRelatedCode) • [поиск ошибок с помощью сопоставления](#FindBugs)  
  
## <a name="see-also"></a>См. также  
 [Сопоставление зависимостей в решениях](../modeling/map-dependencies-across-your-solutions.md)   
 [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Поиск потенциальных проблем, с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Просмотр и реорганизация карт кода](../modeling/browse-and-rearrange-code-maps.md)
