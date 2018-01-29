---
title: "Фрагменты кода | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e2b973b00e132973b8569bc5cad8c1f1318317cd
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2018
---
# <a name="code-snippets"></a>Фрагменты кода

Фрагменты кода — это небольшие блоки многократно используемого кода, которые можно вставлять в файл кода с помощью команды контекстного меню или сочетания клавиш. Они обычно содержат часто используемый код, например конструкции TRY-FINALLY или IF-ELSE, но могут также использоваться и для вставки целых классов или методов.

## <a name="expansion-snippets-and-surround-with-snippets"></a>Фрагменты расширения и фрагменты окружения

В Visual Studio существует два типа фрагментов кода: фрагменты расширения, которые добавляются в указанное курсором место и могут заменить собой ярлык фрагмента, и фрагменты окружения (только в C# и C++), которые добавляются вокруг выделенного блока кода.

Пример кода расширения. В C# ярлык TRYF служит для вставки блока TRY-FINALLY:

```csharp
try
{

}
finally
{

}
```

Чтобы вставить этот фрагмент, выберите в контекстном меню окна кода команду **Вставить фрагмент**, затем команду **Visual C#**, после чего введите `tryf` и нажмите клавишу **TAB** или введите `tryf` и дважды нажмите клавишу **TAB**.

Пример фрагмента окружения. В C++ ярлык `if` может использоваться для вставки фрагмента или для добавления фрагмента обрамления. Если выбрать строку кода (например, `return FALSE;`) и последовательно выбрать команды **Разместить во фрагменте** и **if**, фрагмент кода будет развернут около этой строки:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Параметры замены фрагмента кода

Фрагменты кода могут содержать параметры замены, представляющие собой заполнители, которые необходимо заменить на конкретные значения при написании кода. В предыдущем примере `true` — это параметр замены, который будет заменен на подходящее условие. При замене изменения повторяются для каждого вхождения одного и того же параметра в фрагменте.

Например, в Visual Basic имеется фрагмент кода, который вставляет свойство. В контекстном меню окна кода выберите последовательно команды **Вставить фрагмент**, **Шаблоны кода** и **Свойства, процедуры, события**, а затем определите свойство. Вставлен следующий код:

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

Если изменить `newPropertyValue` на `m_property`, изменяется каждое вхождение `newPropertyValue`. Если изменить `String` на `Int` в объявлении свойства, то значение метода SET также изменится на `Int`.

## <a name="code-snippet-manager"></a>Диспетчер фрагментов кода

Вы можете просмотреть все фрагменты кода, установленные в настоящий момент, а также их расположение на диске, выбрав команду **Инструменты**, **Диспетчер фрагментов кода**. Список фрагментов отсортирован по языку.

Вы можете добавлять и удалять каталоги фрагментов с помощью кнопок **Добавить** и **Удалить** в диалоговом окне **Диспетчер фрагментов кода**. Чтобы добавить отдельные фрагменты, используйте кнопку **Импорт**.

## <a name="see-also"></a>См. также

[Пошаговое руководство. Создание фрагмента кода](../ide/walkthrough-creating-a-code-snippet.md)  
[Практическое руководство. Распространение фрагментов кода](../ide/how-to-distribute-code-snippets.md)  
[Рекомендации по использованию фрагментов кода](../ide/best-practices-for-using-code-snippets.md)  
[Устранение неполадок, связанных с использованием фрагментов](../ide/troubleshooting-snippets.md)  
[Фрагменты кода Visual C#](../ide/visual-csharp-code-snippets.md)  
[Фрагменты кода Visual C++](../ide/visual-cpp-code-snippets.md)  
[Справочник по схеме фрагментов кода](../ide/code-snippets-schema-reference.md)