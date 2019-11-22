---
title: Сопоставление методов в визуализации стека вызовов при отладке
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
caps.latest.revision: 43
author: MikeJo5000
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2a2c6e95822794394dbdfc7f53104b31b7c17ea9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296070"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Сопоставление методов в визуализации стека вызовов при отладке в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для визуального отслеживания стека вызовов при отладке можно создать сопоставление кода. В это сопоставление можно вносить примечания для отслеживания операций, выполняемых кодом. Таким образом, вы сможете сосредоточиться на поиске ошибок.

 ![Debugging with call stacks on code maps](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Требуется:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Код, поддерживающий отладку: Visual C# .NET, Visual Basic .NET, C++, JavaScript и X++

  See: [Video: Debug visually with Code Map debugger integration (Channel 9)](https://go.microsoft.com/fwlink/?LinkId=293418) • [Map the call stack](#MapStack) • [Make notes about the code](#MakeNotes) • [Update the map with the next call stack](#UpdateMap) • [Add related code to the map](#AddRelatedCode) • [Find bugs using the map](#FindBugs) • [Q & A](#QA)

  For details of the commands and actions you can use when working with code maps, see [Browse and rearrange code maps](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a> Сопоставление стека вызова

1. Приступите к отладке. (Keyboard: **F5**)

2. After your app enters break mode or you step into a function, choose **Code Map**. (Keyboard: **Ctrl** + **Shift** +  **`** )

     ![Choose Code Map to start mapping call stack](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     Текущий стек вызовов выделен в новой карте кода оранжевым цветом:

     ![See call stack on code map](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     Эта карта будет автоматически обновляться в ходе отладки. See [Update the map with the next call stack](#UpdateMap).

## <a name="MakeNotes"></a> Добавление примечаний к коду
 Добавьте комментарии для отслеживания операций, выполняемых в коде. To add a new line in a comment, press **Shift + Return**.

 ![Add comment to call stack on code map](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> Обновление сопоставления путем добавления следующего стека вызовов
 Выполните приложение до следующей точки останова или зайдите в функцию. В сопоставление будет добавлен новый стек вызовов.

 ![Update code map with next call stack](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="AddRelatedCode"></a> Добавление связанного кода в сопоставление
 Итак, сопоставление готово. Что дальше? При работе с Visual C#, .NET или Visual Basic .NET добавьте в него элементы, такие как поля, свойства и методы, для отслеживания операций в коде.

 Дважды щелкните метод для просмотра его определения кода или используйте контекстное меню метода. (Keyboard: Select the method on the map and press **F12**)

 ![Go to code definition for a method on code map](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Добавьте элементы, которые необходимо отслеживать в сопоставлении.

 ![Show fields in a method on call stack code map](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> По умолчанию при добавлении элементов в сопоставление также добавляются узлы родительской группы, соответствующие, например, классу, пространству имен или сборке. While this is useful, you can keep the map simple by turning off this feature using the **Include Parents** button on the map toolbar, or by pressing **CTRL** when you add items.

 ![Fields related to a method on call stack code map](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 Нетрудно определить, какие методы используют одинаковые поля. Последние добавленные элементы отображаются зеленым цветом.

 Продолжайте формировать сопоставление, чтобы увидеть дополнительный код.

 ![See methods that use a field: call stack code map](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Methods that use a field on call stack code map](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> Поиск ошибок с помощью сопоставления
 Визуализация кода поможет вам быстрее находить ошибки. Например, предположим, что вы ищите ошибку в программе для рисования. Когда вы создаете линию и пробуете отменить ее создание, ничего не происходит до тех пор, пока не будет нарисована следующая линия.

 Установив точки останова в методах `clear`, `undo` и `Repaint`, вы начинаете отладку и создаете сопоставление, аналогичное представленному ниже:

 ![Add another call stack to code map](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Учтите, что все жесты пользователя в сопоставлении вызывают метод `Repaint`, за исключением `undo`. Возможно, именно поэтому функция `undo` срабатывает не сразу.

 Когда вы исправите ошибку и продолжите выполнение программы, в сопоставление будет добавлен новый вызов из `undo` в `Repaint`.

 ![Add new method call to call stack on code map](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="QA"></a> Вопросы и ответы

- **Not all calls appear on the map. Why?**

   По умолчанию в сопоставлении отображается только ваш код. To see external code, turn it on in the **Call Stack** window:

   ![Display external code using the Call Stack window](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   or turn off **Enable Just My Code** in the Visual Studio debugging options:

   ![Show external code using Options dialog](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **Does changing the map affect the code?**

   Изменение сопоставления никак не влияет на код. Можно свободно переименовать, изменить или удалить любой элемент в сопоставлении.

- **What does this message mean: “The diagram may be based on an older version of the code”?**

   С момента последнего обновления сопоставления код мог измениться. Например, вызов в сопоставлении может уже не существовать в коде. Закройте сообщение, а затем попытайтесь повторить сборку решения, прежде чем повторно обновлять сопоставление.

- **How do I control the map’s layout?**

   Open the **Layout** menu on the map toolbar:

  - Измените макет по умолчанию.

  - To stop rearranging the map automatically, turn off **Automatically Layout when Debugging**.

  - To rearrange the map as little as possible when you add items, turn off **Incremental Layout**.

- **Can I share the map with others?**

   Сопоставление можно экспортировать, отправить его другим пользователям при наличии Microsoft Outlook или сохранить его в решении, чтобы можно было вернуть его в систему управления версиями Team Foundation.

   ![Share call stack code map with others](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **How do I stop the map from adding new call stacks automatically?**

   Choose ![Button &#45; Show call stack on code map automatically](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") on the map toolbar. To manually add the current call stack to the map, press **Ctrl** + **Shift** +  **`** .

   Существующие стеки вызовов по-прежнему будут выделяться на сопоставлении во время отладки.

- **What do the item icons and arrows mean?**

   Чтобы узнать дополнительные сведения об элементе, наведите на него указатель мыши и прочитайте подсказку. You can also look at the **Legend** to learn what each icon means.

   ![What do icons on the call stack code map mean?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  See: [Map the call stack](#MapStack) • [Make notes about the code](#MakeNotes) • [Update the map with the next call stack](#UpdateMap) • [Add related code to the map](#AddRelatedCode) • [Find bugs using the map](#FindBugs)

## <a name="see-also"></a>См. также раздел
 [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md) [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md) [Find potential problems using code map analyzers](../modeling/find-potential-problems-using-code-map-analyzers.md) [Browse and rearrange code maps](../modeling/browse-and-rearrange-code-maps.md)
