---
title: Фрагменты кода C#
description: Узнайте, как с помощью фрагментов кода в Visual Studio можно добавлять часто используемый код в файлы кода C#.
ms.custom: SEO-VS-2020
ms.date: 06/05/2017
ms.topic: reference
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e4656e0769075be26db5bd06108093a49fb5e2af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941545"
---
# <a name="c-code-snippets"></a>Фрагменты кода C#

Фрагменты кода — это готовые фрагменты кода, которые можно быстро вставлять в свой код. Например, фрагмент кода `for` создает пустой цикл `for`. Некоторые фрагменты кода являются окружающими, т. е. позволяют сначала выбрать строки кода, а затем фрагмент кода, в который будут включены выбранные строки. Например, если выбрать строки кода и затем активировать фрагмент кода `for`, будет создан блок цикла `for`, внутри которого будут находиться выбранные строки кода. Фрагменты кода ускоряют, упрощают написание программ и делают этот процесс более надежным.

Можно вставить фрагмент кода в месте расположения курсора или вставить окружающий фрагмент кода вокруг выделенного в данный момент кода. Меню вставки фрагмента кода вызывается с помощью команд **Вставить фрагмент кода** или **Разместить во фрагменте** из меню **IntelliSense** либо с помощью сочетаний клавиш **CTRL**+**K**,**X** или **CTRL**+**K**,**S** соответственно.

**Меню вставки фрагментов кода** показывает имена всех доступных фрагментов кода. Меню вставки фрагментов кода также обеспечивает возможность ввода в диалоговом окне имени фрагмента кода или части имени фрагмента кода. Меню вставки фрагментов кода выделяет наиболее точно совпадающее имя фрагмента кода. Нажатие клавиши **TAB** в любой момент приводит к отмене использования меню вставки фрагментов кода и вставке выбранного в данный момент фрагмента кода. Нажатие клавиши **ESC** или щелчок мышью в окне редактора кода приводит к отмене использования средства вставки фрагментов кода без вставки выбранного в данный момент фрагмента кода.

## <a name="default-code-snippets"></a>Фрагменты кода по умолчанию

По умолчанию в Visual Studio для C# включены указанные ниже фрагменты кода.

|Имя (или сокращенное имя)|Описание|Допустимые места для вставки фрагмента|
| - |-----------------| - |
|#if|Создает директивы [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) и [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif).|В любом месте.|
|#region|Создает директивы [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) и [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion).|В любом месте.|
|~|Создает [метод завершения](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (деструктор) для включающего класса.|Внутри класса.|
|Атрибут|Создает объявление класса, производного от <xref:System.Attribute>.|Внутри пространства имен (включая глобальное пространство имен), класса или структуры.|
|checked|Создает блок [checked](/dotnet/csharp/language-reference/keywords/checked).|Внутри метода, индексатора, метода доступа к свойству или событию.|
|class|Создает объявление класса.|Внутри пространства имен (включая глобальное пространство имен), класса или структуры.|
|ctor|Создает конструктор для включающего класса.|Внутри класса.|
|cw|Создает вызов <xref:System.Console.WriteLine%2A>.|Внутри метода, индексатора, метода доступа к свойству или событию.|
|do|Создает цикл [do](/dotnet/csharp/language-reference/keywords/do) `while`.|Внутри метода, индексатора, метода доступа к свойству или событию.|
|else|Создает [else](/dotnet/csharp/language-reference/keywords/if-else) блок.|Внутри метода, индексатора, метода доступа к свойству или событию.|
|enum|Создает объявление типа [enum](/dotnet/csharp/language-reference/keywords/enum).|Внутри пространства имен (включая глобальное пространство имен), класса или структуры.|
|equals|Создает объявление метода, которое переопределяет метод <xref:System.Object.Equals%2A>, определенный в классе <xref:System.Object>.|Внутри класса или структуры.|
|exception|Создает объявление класса, производного от исключения (по умолчанию <xref:System.Exception>).|Внутри пространства имен (включая глобальное пространство имен), класса или структуры.|
|для|Создает цикл [for](/dotnet/csharp/language-reference/keywords/for).|Внутри метода, индексатора, метода доступа к свойству или событию.|
|foreach|Создает цикл [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).|Внутри метода, индексатора, метода доступа к свойству или событию.|
|forr|Создает цикл [for](/dotnet/csharp/language-reference/keywords/for), уменьшающий переменную цикла после каждой итерации.|Внутри метода, индексатора, метода доступа к свойству или событию.|
|if|Создает блок [if](/dotnet/csharp/language-reference/keywords/if-else).|Внутри метода, индексатора, метода доступа к свойству или событию.|
|Индексатор|Создает объявление индексатора.|Внутри класса или структуры.|
|interface|Создает объявление [interface](/dotnet/csharp/language-reference/keywords/interface).|Внутри пространства имен (включая глобальное пространство имен), класса или структуры.|
|invoke|Создает блок, который безопасно вызывает событие.|Внутри метода, индексатора, метода доступа к свойству или событию.|
|iterator|Создает итератор.|Внутри класса или структуры.|
|iterindex|Создает именованную пару из итератора и индексатора с помощью вложенного класса.|Внутри класса или структуры.|
|lock|Создает блок [lock](/dotnet/csharp/language-reference/keywords/lock-statement).|Внутри метода, индексатора, метода доступа к свойству или событию.|
|mbox|Создает вызов <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Также может потребоваться добавить ссылку на библиотеку *System.Windows.Forms.dll*.|Внутри метода, индексатора, метода доступа к свойству или событию.|
|namespace|Создает объявление [namespace](/dotnet/csharp/language-reference/keywords/namespace).|Внутри пространства имен (включая глобальное пространство имен).|
|prop|Создает объявление [автоматически реализуемого свойства](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).|Внутри класса или структуры.|
|propfull|Создает объявление свойства с методами доступа `get` и `set`.|Внутри класса или структуры.|
|propg|Создает доступное только для чтения [автоматически реализуемое свойство](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) с закрытым методом доступа `set`.|Внутри класса или структуры.|
|sim|Создает объявление метода [static](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int) Main.|Внутри класса или структуры.|
|struct|Создает объявление [struct](/dotnet/csharp/language-reference/keywords/struct).|Внутри пространства имен (включая глобальное пространство имен), класса или структуры.|
|svm|Создает объявление метода [static](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/void) Main.|Внутри класса или структуры.|
|switch|Создает блок [switch](/dotnet/csharp/language-reference/keywords/switch).|Внутри метода, индексатора, метода доступа к свойству или событию.|
|попробуйте выполнить следующее|Создает блок [try-catch](/dotnet/csharp/language-reference/keywords/try-catch).|Внутри метода, индексатора, метода доступа к свойству или событию.|
|tryf|Создает блок [try-finally](/dotnet/csharp/language-reference/keywords/try-finally).|Внутри метода, индексатора, метода доступа к свойству или событию.|
|unchecked|Создает блок [unchecked](/dotnet/csharp/language-reference/keywords/unchecked).|Внутри метода, индексатора, метода доступа к свойству или событию.|
|unsafe|Создает блок [unsafe](/dotnet/csharp/language-reference/keywords/unsafe).|Внутри метода, индексатора, метода доступа к свойству или событию.|
|using|Создает директиву [using](/dotnet/csharp/language-reference/keywords/using-directive).|Внутри пространства имен (включая глобальное пространство имен).|
|while|Создает цикл [while](/dotnet/csharp/language-reference/keywords/while).|Внутри метода, индексатора, метода доступа к свойству или событию.|

## <a name="see-also"></a>См. также раздел

- [Функции фрагмента кода](../ide/code-snippet-functions.md)
- [Фрагменты кода](../ide/code-snippets.md)
- [Параметры шаблона](../ide/template-parameters.md)
- [Практическое руководство. Использование окружающих фрагментов кода](../ide/how-to-use-surround-with-code-snippets.md)
