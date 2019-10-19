---
title: "\"Параметры\", \"Текстовый редактор\", \"C#\", IntelliSense | Документы Майкрософт"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e3f4df9a7a885245e40f7e9fec1b0da207ada39
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662300"
---
# <a name="options-text-editor-c-intellisense"></a>"Параметры", "Текстовый редактор", C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Страница **IntelliSense** служит для изменения параметров, влияющих на поведение IntelliSense для Visual C#. Чтобы получить доступ к странице свойств **IntelliSense**, щелкните **Параметры** в меню **Сервис**, затем щелкните **C#** в папке **Текстовый редактор** и выберите **IntelliSense.**

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Страница **IntelliSense** содержит следующие свойства:

## <a name="completion-lists"></a>Списки завершения
 **Показывать список завершения после ввода символа** Если выбран этот параметр, IntelliSense автоматически отображает список завершения при начале ввода. Если этот параметр не выбран, функцию завершения IntelliSense можно вызвать из **IntelliSense** или с помощью сочетания клавиш CTRL+ПРОБЕЛ.

 **Располагать ключевые слова в списках завершения** Если выбран этот параметр, IntelliSense добавляет C# ключевые слова, например [класс](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), в список завершения.

 **Размещение фрагментов кода в списках завершения** Если выбран этот параметр, IntelliSense добавляет псевдонимы фрагментов C# кода в список завершения. Если псевдоним фрагмента кода совпадает с ключевым словом, например [class](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), оно заменяется ярлыком. Дополнительные сведения см. в разделе [Фрагменты кода Visual C#](../../ide/visual-csharp-code-snippets.md).

## <a name="selection-in-completion-lists"></a>Выделение в списках завершения
 **Зафиксировано, введите следующие символы:** Задает все символы, которые выполняют автоматическое завершение IntelliSense для выбранного элемента в списке завершения после их ввода.

 **Зафиксировано нажатием клавиши пробел** Указывает действие нажатия клавиши пробел для выполнения автоматического завершения IntelliSense для выбранного элемента в списке завершения.

 **Добавить новую строку при вводе в конце полностью введенного слова** Указывает, что если ввести все символы для записи в списке завершения и нажать клавишу ВВОД, автоматически создается новая строка, а курсор переместится на новую строку.

 Например, если ввести `else` и нажать клавишу ВВОД, в редакторе появится следующее:

 `else`

 `|` (положение курсора)

 Однако, если ввести только `el` и нажать клавишу ВВОД, в редакторе появится следующее:

 `else|` (положение курсора)

## <a name="intellisense-member-selection"></a>Выбор членов технологией IntelliSense
 **Предварительно выбирает недавно использованный член** Если выбран этот параметр, IntelliSense предварительно выбирает недавно выбранные элементы во всплывающем окне Список членов для автоматического завершения имени объекта во время текущего сеанса в интегрированной среде разработки (IDE). Журнал наиболее часто используемых членов списка очищается после завершения каждого сеанса в интегрированной среде разработки. Дополнительные сведения см. в разделе [IntelliSense для недавно использовавшихся членов](../../misc/intellisense-for-most-recently-used-members.md).

## <a name="see-also"></a>См. также
 [Общие, среда, диалоговое окно "Параметры"](../../ide/reference/general-environment-options-dialog-box.md) [Комментарии XML-документации](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [с использованием IntelliSense](../../ide/using-intellisense.md)
