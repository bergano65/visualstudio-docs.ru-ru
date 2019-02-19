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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7c1bf08c5e97a2504d797a58e96cd12cdcf08cc8
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54793194"
---
# <a name="options-text-editor-c-intellisense"></a>"Параметры", "Текстовый редактор", C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Страница **IntelliSense** служит для изменения параметров, влияющих на поведение IntelliSense для Visual C#. Чтобы получить доступ к странице свойств **IntelliSense**, щелкните **Параметры** в меню **Сервис**, затем щелкните **C#** в папке **Текстовый редактор** и выберите **IntelliSense.**  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Страница **IntelliSense** содержит следующие свойства:  
  
## <a name="completion-lists"></a>Списки завершения  
 **Показывать список завершения после ввода знака**  
 Если этот параметр выбран, IntelliSense автоматически отображает список завершения при начале ввода. Если этот параметр не выбран, функцию завершения IntelliSense можно вызвать из **IntelliSense** или с помощью сочетания клавиш CTRL+ПРОБЕЛ.  
  
 **Помещать ключевые слова в списки завершения**  
 Если этот параметр выбран, IntelliSense добавляет ключевые слова C#, например [class](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), в список завершения.  
  
 **Помещать фрагменты кода в списки завершения**  
 Если этот параметр выбран, IntelliSense добавляет псевдонимы для фрагментов кода C# в список завершения. Если псевдоним фрагмента кода совпадает с ключевым словом, например [class](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), оно заменяется ярлыком. Дополнительные сведения см. в разделе [Фрагменты кода Visual C#](../../ide/visual-csharp-code-snippets.md).  
  
## <a name="selection-in-completion-lists"></a>Выделение в списках завершения  
 **Зафиксирован после ввода следующих знаков**  
 Указывает все символы, используемые IntelliSense для автоматического завершения выбранного элемента в списке завершения, после их ввода.  
  
 **Подтверждено нажатием пробела**  
 Включает автоматическое завершение IntelliSense для выбранного элемента в списке завершения по нажатию клавиши ПРОБЕЛ.  
  
 **Добавлять новую строку по нажатию клавиши ВВОД в конце полностью введенного слова**  
 Указывает, что если вы вводите все символы для записи в списке завершения и нажимаете клавишу ВВОД, то автоматически создается новая строка, а курсор перемещается на новую строку.  
  
 Например, если ввести `else` и нажать клавишу ВВОД, в редакторе появится следующее:  
  
 `else`  
  
 `|` (положение курсора)  
  
 Однако, если ввести только `el` и нажать клавишу ВВОД, в редакторе появится следующее:  
  
 `else|` (положение курсора)  
  
## <a name="intellisense-member-selection"></a>Выбор членов технологией IntelliSense  
 **Предварительно выделять последний использованный член**  
 Если выбран этот параметр, IntelliSense предварительно выбирает последние элементы, выбранные во всплывающем окне "Список членов" для автоматического завершения имени объекта, в рамках текущего сеанса в среде IDE. Журнал наиболее часто используемых членов списка очищается после завершения каждого сеанса в интегрированной среде разработки. Дополнительные сведения см. в разделе [IntelliSense для недавно использовавшихся членов](../../misc/intellisense-for-most-recently-used-members.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Страница "Общие", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/general-environment-options-dialog-box.md)   
 [Комментарии XML-документации](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [Использование технологии IntelliSense](../../ide/using-intellisense.md)
