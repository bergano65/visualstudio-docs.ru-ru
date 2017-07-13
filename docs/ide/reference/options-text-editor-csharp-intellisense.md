---
title: "&quot;Параметры&quot;, &quot;Текстовый редактор&quot;, &quot;C#&quot;, IntelliSense | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 25
author: kempb
ms.author: kempb
manager: ghogen
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: b34b280b3558003c5c3ad92515d773bc7d45fdda
ms.contentlocale: ru-ru
ms.lasthandoff: 05/24/2017

---
# "Параметры", "Текстовый редактор", C#, IntelliSense
<a id="options-text-editor-c-intellisense" class="xliff"></a>
Страница **IntelliSense** служит для изменения параметров, влияющих на поведение IntelliSense для Visual C#. Чтобы получить доступ к странице свойств **IntelliSense**, щелкните **Параметры** в меню **Сервис**, затем щелкните **C#** в папке **Текстовый редактор** и выберите **IntelliSense.**  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
 Страница **IntelliSense** содержит следующие свойства:  
  
## Списки завершения
<a id="completion-lists" class="xliff"></a>  
 **Показывать список завершения после ввода знака**  
 Если этот параметр выбран, IntelliSense автоматически отображает список завершения при начале ввода. Если этот параметр не выбран, функцию завершения IntelliSense можно вызвать из **IntelliSense** или с помощью сочетания клавиш CTRL+ПРОБЕЛ.  
  
 **Помещать ключевые слова в списки завершения**  
 Если этот параметр выбран, IntelliSense добавляет ключевые слова C#, например [class](/dotnet/csharp/language-reference/keywords/class), в список завершения.  
  
 **Помещать фрагменты кода в списки завершения**  
 Если этот параметр выбран, IntelliSense добавляет псевдонимы для фрагментов кода C# в список завершения. Если псевдоним фрагмента кода совпадает с ключевым словом, например [class](/dotnet/csharp/language-reference/keywords/class), оно заменяется ярлыком. Дополнительные сведения см. в разделе [Фрагменты кода Visual C#](../../ide/visual-csharp-code-snippets.md).  
  
## Выделение в списках завершения
<a id="selection-in-completion-lists" class="xliff"></a>  
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
  
## Выбор членов технологией IntelliSense
<a id="intellisense-member-selection" class="xliff"></a>  
 **Предварительно выделять последний использованный член**  
 Если выбран этот параметр, IntelliSense предварительно выбирает последние элементы, выбранные во всплывающем окне "Список членов" для автоматического завершения имени объекта, в рамках текущего сеанса в среде IDE. Журнал наиболее часто используемых членов списка очищается после завершения каждого сеанса в интегрированной среде разработки. Дополнительные сведения см. в разделе [IntelliSense для недавно использовавшихся членов](../../ide/visual-csharp-intellisense.md#most-recently-used-members).  
  
## См. также
<a id="see-also" class="xliff"></a>  
 [Страница "Общие", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/general-environment-options-dialog-box.md)   
 [Комментарии XML-документации](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [Использование технологии IntelliSense](../../ide/using-intellisense.md)
