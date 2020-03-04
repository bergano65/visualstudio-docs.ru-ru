---
title: Вставка комментариев XML-документации
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e21d0617f954c0cc34975b7f8626b83966f6b5d
ms.sourcegitcommit: 9de7d25056da59df0941508c80c0b12766ba6580
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706402"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Практическое руководство. вставку XML-комментариев для создания документации

Visual Studio может помочь вам документировать элементы кода, такие как классы и методы, автоматически формируя стандартную структуру комментариев для XML-документации. Во время компиляции можно создать XML-файл, содержащий комментарии для документации.

> [!TIP]
> Сведения о настройке имени и расположения созданного XML-файла см. в статье [Документирование кода с помощью XML-комментариев](/dotnet/csharp/codedoc).

Созданный компилятором XML-файл можно распространять вместе со сборкой .NET, чтобы Visual Studio и другие интегрированные среды разработки могли использовать IntelliSense для отображения кратких сведений о типах и элементах. Кроме того, XML-файл можно запускать с помощью таких средств, как [DocFX](https://dotnet.github.io/docfx/) и [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526), и создавать веб-сайты со справочными сведениями по API.

> [!NOTE]
> Команда **Вставить комментарий**, которая автоматически вставляет комментарии XML-документации, доступна в [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) и [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). Однако можно вручную вставить [комментарии XML-документации в файлы C++](/cpp/build/reference/xml-documentation-visual-cpp) и по-прежнему создавать файлы XML-документации во время компиляции.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Вставка XML-комментариев для элемента кода

1. Поместите текстовый курсор над элементом, например методом, который нужно задокументировать.

2. Выполните одно из следующих действий.

   - Введите `///` в C# или `'''` в Visual Basic

   - В меню **Правка** выберите **IntelliSense** > **Вставить комментарий**.

   - Щелкните правой кнопкой мыши или вызовите контекстное меню в редакторе кода или над ним и выберите **Фрагмент кода** > **Вставить комментарий**.

   Над элементом кода сразу же создается XML-шаблон. Например, при комментировании метода создается элемент **\<summary\>** , элемент **\<param\>** для каждого параметра и элемент **\<returns\>** для документирования возвращаемого значения.

   ![Шаблон для XML-комментариев — C#](media/doc-preview-cs.png)

   ![Шаблон для XML-комментариев — Visual Basic](media/doc-preview-vb.png)

3. Введите описание для каждого XML-элемента, чтобы полностью задокументировать элемент кода.

   ![Ввод комментариев](media/doc-result-cs.png)

Стили можно использовать в комментариях XML, которые будут отображаться в виде кратких сведений при наведении указателя мыши на элемент. К этим стилям относятся курсив, полужирный шрифт, маркеры и ссылка, доступная для щелчка.

   ![Ввод комментариев](media/doc-style-cs.png) 

> [!NOTE]
> Существует [параметр](../../ide/reference/options-text-editor-csharp-advanced.md) для переключения комментариев XML-документации после ввода `///` в C# или `'''` Visual Basic. В строке меню выберите **Сервис** > **Параметры**, чтобы открыть диалоговое окно **Параметры**. Перейдите в раздел **Текстовый редактор** > **C#** или **Basic** > **Дополнительно**. В разделе **Справка редактора** найдите параметр **Создавать комментарии XML-документации**.

## <a name="see-also"></a>См. также

- [Комментарии к XML-документации (руководство по программированию на C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Документирование кода с помощью XML-комментариев (руководство по C#)](/dotnet/csharp/codedoc)
- [Практическое руководство. создание XML-документации (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Комментарии C++](/cpp/cpp/comments-cpp)
- [XML-документация (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Создание кода](../code-generation-in-visual-studio.md)
