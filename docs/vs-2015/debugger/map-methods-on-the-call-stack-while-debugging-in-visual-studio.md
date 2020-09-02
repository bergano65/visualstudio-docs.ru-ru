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
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e8376884f72aeca2f3bf56f0d7bbc1636379a18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847305"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Сопоставление методов в визуализации стека вызовов при отладке в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для визуального отслеживания стека вызовов при отладке можно создать сопоставление кода. В это сопоставление можно вносить примечания для отслеживания операций, выполняемых кодом. Таким образом, вы сможете сосредоточиться на поиске ошибок.

 ![Отладка со стеками вызовов на картах кода](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Требуется:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Код, поддерживающий отладку: Visual C# .NET, Visual Basic .NET, C++, JavaScript и X++

  См. [видео: Отладка визуального элемента с помощью функции интеграции с отладчиком карт кода (канал 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration) • [карта стека вызовов](#MapStack) • [Создание примечаний о коде](#MakeNotes) • [Обновление карты со следующим стеком вызовов](#UpdateMap) • [Добавление связанного кода в карту](#AddRelatedCode) • [Поиск ошибок с помощью карты](#FindBugs) • [Q & A](#QA)

  Дополнительные сведения о командах и действиях, которые можно использовать при работе с картами кода, см. в разделе [Обзор и реорганизация карт кода](../modeling/browse-and-rearrange-code-maps.md).

## <a name="map-the-call-stack"></a><a name="MapStack"></a> Сопоставление стека вызова

1. Запустите отладку. (Клавиатура: **F5**)

2. После того как приложение переходит в режим приостановки выполнения или вы выполняете шаг с заходом в функцию, выберите **карту кода**. (Клавиатура: **CTRL**  +  **SHIFT**  +  **`** )

     ![Выберите "Карта кода", чтобы начать формирование карты для стека вызовов](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     Текущий стек вызовов выделен в новой карте кода оранжевым цветом:

     ![См. стек вызовов на карте кода](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     Эта карта будет автоматически обновляться в ходе отладки. См. раздел [обновление схемы с помощью следующего стека вызовов](#UpdateMap).

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> Добавление примечаний к коду
 Добавьте комментарии для отслеживания операций, выполняемых в коде. Чтобы добавить новую строку в комментарий, нажмите клавиши **Shift + Return**.

 ![Добавление комментария к стеку вызовов на карте кода](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> Обновление сопоставления путем добавления следующего стека вызовов
 Выполните приложение до следующей точки останова или зайдите в функцию. В сопоставление будет добавлен новый стек вызовов.

 ![Обновление карты кода следующим стеком вызовов](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> Добавление связанного кода в сопоставление
 Итак, сопоставление готово. Что дальше? При работе с Visual C#, .NET или Visual Basic .NET добавьте в него элементы, такие как поля, свойства и методы, для отслеживания операций в коде.

 Дважды щелкните метод для просмотра его определения кода или используйте контекстное меню метода. (Клавиатура: выберите метод на карте и нажмите клавишу **F12**)

 ![Переход к определению кода метода на карте кода](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Добавьте элементы, которые необходимо отслеживать в сопоставлении.

 ![Отображение полей в методе на карте кода со стеком вызовов](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> По умолчанию при добавлении элементов в сопоставление также добавляются узлы родительской группы, соответствующие, например, классу, пространству имен или сборке. Хотя это и полезно, можно сделать карту простой, отключив эту функцию с помощью кнопки **включить родителей** на панели инструментов Map или нажав **клавишу CTRL** при добавлении элементов.

 ![Поля, связанные с методом на карте кода со стеком вызовов](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 Нетрудно определить, какие методы используют одинаковые поля. Последние добавленные элементы отображаются зеленым цветом.

 Продолжайте формировать сопоставление, чтобы увидеть дополнительный код.

 ![См. методы, использующие поле: карта кода со стеком вызовов](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Методы, использующие поле на карте кода со стеком вызовов](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> Поиск ошибок с помощью сопоставления
 Визуализация кода поможет вам быстрее находить ошибки. Например, предположим, что вы ищите ошибку в программе для рисования. Когда вы создаете линию и пробуете отменить ее создание, ничего не происходит до тех пор, пока не будет нарисована следующая линия.

 Установив точки останова в методах `clear`, `undo` и `Repaint`, вы начинаете отладку и создаете сопоставление, аналогичное представленному ниже:

 ![Добавление другого стека вызовов на карту кода](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Учтите, что все жесты пользователя в сопоставлении вызывают метод `Repaint`, за исключением `undo`. Возможно, именно поэтому функция `undo` срабатывает не сразу.

 Когда вы исправите ошибку и продолжите выполнение программы, в сопоставление будет добавлен новый вызов из `undo` в `Repaint`.

 ![Добавление нового вызова метода в стек вызовов на карте кода](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="q--a"></a><a name="QA"></a> Вопросы и ответы

- **На карте отображаются не все вызовы. Важно?**

   По умолчанию в сопоставлении отображается только ваш код. Чтобы просмотреть внешний код, включите его в окне **Стек вызовов** :

   ![Отображение внешнего кода с помощью окна стека вызовов](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   или отключите параметр **включить только мой код** в вариантах отладки Visual Studio:

   ![Отображение внешнего кода с помощью диалогового окна параметров](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **Изменение сопоставления влияет на код?**

   Изменение сопоставления никак не влияет на код. Можно свободно переименовать, изменить или удалить любой элемент в сопоставлении.

- **Что означает сообщение: "Диаграмма может быть составлена с использованием более старой версии кода"?**

   С момента последнего обновления сопоставления код мог измениться. Например, вызов в сопоставлении может уже не существовать в коде. Закройте сообщение, а затем попытайтесь повторить сборку решения, прежде чем повторно обновлять сопоставление.

- **Как управлять макетом сопоставления?**

   Откройте меню **Макет** на панели инструментов Map:

  - Изменить макет по умолчанию.

  - Чтобы отключить автоматическое перераспределение карт, отключите **Автоматический макет при отладке**.

  - Чтобы изменить расположение на карте как можно меньше при добавлении элементов, отключите **добавочный макет**.

- **Можно ли использовать сопоставление совместно с другими пользователями?**

   Сопоставление можно экспортировать, отправить его другим пользователям при наличии Microsoft Outlook или сохранить его в решении, чтобы можно было вернуть его в систему управления версиями Team Foundation.

   ![Предоставление другим пользователям доступа к карте кода со стеком вызовов](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **Как не допустить, чтобы сопоставление добавляло новые стеки вызова автоматически?**

   Нажмите ![кнопку &#45; отображать стек вызовов на карте кода автоматически](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") на панели инструментов Map. Чтобы вручную добавить текущий стек вызовов на карту, нажмите клавиши **CTRL** + **SHIFT** +  **`** .

   Существующие стеки вызовов по-прежнему будут выделяться на сопоставлении во время отладки.

- **Что означают значки элементов и стрелки?**

   Чтобы узнать дополнительные сведения об элементе, наведите на него указатель мыши и прочитайте подсказку. Вы также можете просмотреть **Условные обозначения** , чтобы узнать, что означает каждый значок.

   ![Расшифровка значков на карте кода со стеком вызовов](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  См. раздел [Привязка стека вызовов](#MapStack) • [Создание заметок о коде](#MakeNotes) • [обновление схемы с помощью следующего стека вызовов](#UpdateMap) • [Добавление связанного кода к карте](#AddRelatedCode) • [Поиск ошибок с помощью Map](#FindBugs) .

## <a name="see-also"></a>См. также:
 [Сопоставление зависимостей в решениях](../modeling/map-dependencies-across-your-solutions.md) [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md) [Поиск потенциальных проблем с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md) [Просмотр и реорганизация карт кода](../modeling/browse-and-rearrange-code-maps.md)
