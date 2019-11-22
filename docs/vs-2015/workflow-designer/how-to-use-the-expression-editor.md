---
title: 'How to: Use the Expression Editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d40cefc3dd47f7f4ad7e8255d8bdc06bc5f1651
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300933"
---
# <a name="how-to-use-the-expression-editor"></a>Как использовать редактор выражений
Редактор выражений является элементом управления [!INCLUDE[wfd1](../includes/wfd1-md.md)], который используется во многих действиях рабочего потока в качестве средства их ввода и вычисления. Редактор выражений предоставляет полноценные возможности редактирования интегрированной среды разработки, включая IntelliSense, выделение цветом, сведения о параметре, подчеркивание некоторых типов ошибок волнистыми линиями, а также другие функции. Компилятор проверяет выражение после его ввода. Если выражение является недопустимым, то отображается значок ошибки. The editor can also be opened as an **Expression Editor** dialog box.

 Выражения являются литералами или кодом [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], привязанным к аргументам или свойствам. Они содержат элементы значений (например, переменные, константы, литералы, свойства), которые в сочетании с операциями выдают новое значение. При написании выражения используется синтаксис VB.NET, даже если приложение находится в программе на языке C#. This means capitalization does not matter, comparison is performed using a single equals (“=”) sign instead of (“==”), the Boolean operators are the words "and" and "or" instead of the symbols "&&" and "&#124;&#124;", and **Nothing** is used instead of **null**. For more information on expressions and operators in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] and for some samples, see [Operators and Expressions in Visual Basic](https://go.microsoft.com/fwlink/?LinkId=186818).

 The **Expression Editor** behaves as follows:

- Если редактор выражений не имеет фокуса ввода, то он выглядит как обычный элемент управления TextBlock.

- Как только редактор выражений получает фокус ввода, то он работает как элемент управления «Редактор выражений». При переходе фокуса он снова выглядит как обычный элемент TextBlock.

- Если установить фокус на редактор выражений в повторно размещенном конструкторе рабочих процессов, то он будет работать как элемент TextBlock. При переходе фокуса в повторно размещенный конструктор рабочих процессов редактор выражений снова будет работать как обычный элемент TextBlock.

> [!NOTE]
> Технология Intellisense для редактора выражений доступна только в [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Как в [!INCLUDE[vs2010](../includes/vs2010-md.md)], так и в сценариях с повторным размещением компилятор проверяет выражение после ввода, а редактор выражений показывает значок ошибки, если выражение является недопустимым.

### <a name="using-the-expression-editor"></a>Использование редактора выражений

1. Откройте в [!INCLUDE[vs2010](../includes/vs2010-md.md)] существующий или создайте новый проект рабочего процесса.

2. Добавьте к рабочему процессу какое-нибудь действие, например <xref:System.Activities.Statements.Assign>.

    > [!NOTE]
    > Многие действия рабочих процессов имеют редакторы выражений. Выражение TextBlocks также появляется в конструкторе переменных, конструкторе аргументов и конструкторе динамических аргументов. Действие <xref:System.Activities.Statements.Assign> используется в качестве примера.

3. Щелкните редактор выражений в конструкторе операций для действия <xref:System.Activities.Statements.Assign>.

     The grey watermark strings **\<To>** and **\<Enter a VB Expression>** are the default text strings for expression editors in the <xref:System.Activities.Statements.Assign> activity.

4. Введите выражение. При вводе строки заключайте ее в кавычки. Если аргумент выражения привязывается к переменной, то кавычки не ставятся.

     По завершении выберите область вне редактора выражений для перемещения фокуса в другую часть конструктора. Это приведет к вычислению компилятором выражения, как описано выше.

     Ввести или изменить выражение можно также по нажатию кнопки с многоточием рядом с именем свойства в таблице свойств. This will open the **Expression Editor** as dialog box.

## <a name="see-also"></a>См. также раздел
 <xref:System.Activities.Presentation.View.ExpressionTextBox>