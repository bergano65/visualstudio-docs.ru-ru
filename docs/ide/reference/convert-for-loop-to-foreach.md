---
title: Рефакторинг кода для преобразования цикла for в оператор foreach
ms.date: 05/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 85a8d0c5644d1a7daf342b9524e75f7969b3781a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888196"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Рефакторинг кода для преобразования цикла for в оператор foreach и наоборот

В этой статье описан рефакторинг кода с помощью быстрых действий, который позволяет перейти с одной структуры выполнения цикла на другую. Здесь также описано, почему в некоторых случаях не стоит преобразовывать цикл [for](/dotnet/csharp/language-reference/keywords/for) в оператор [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) в коде.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Преобразование цикла for в оператор foreach

Если у вас есть цикл [for](/dotnet/csharp/language-reference/keywords/for) в коде, можно использовать этот рефакторинг кода для преобразования цикла в оператор [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Область применения этого рефакторинга:

- C#

> [!NOTE]
> Рефакторинг с помощью быстрого действия **Преобразовать в foreach** доступен только для циклов [for](/dotnet/csharp/language-reference/keywords/for), которые содержат все три части: инициализатор, условие и итератор.

### <a name="why-convert"></a>Для чего это нужно

Причины, из-за которых может потребоваться преобразование цикла [for](/dotnet/csharp/language-reference/keywords/for) в оператор [foreach](/dotnet/csharp/language-reference/keywords/foreach-in), включают в себя:

- Вы используете локальную переменную внутри цикла только в качестве индекса для доступа к элементу.

- Вы хотите упростить код и уменьшить вероятность возникновения логических ошибок в инициализаторе, условиях и разделах итератора.

### <a name="how-to-use-it"></a>Использование

1. Поместите курсор на ключевое слово `for`.

1. Нажмите клавиши **CTRL**+**.** или нажмите значок отвертки ![значок отвертки](../media/screwdriver-icon.png) на полях файла кода.

   ![Меню преобразования в foreach](media/convert-to-foreach.png)

1. Выберите **Преобразовать в foreach**. Также можно выбрать **Просмотр изменений**, чтобы открыть диалоговое окно [Просмотр изменений](../../ide/preview-changes.md), и нажать **Применить**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Преобразование оператора foreach в цикл for

Если у вас есть оператор [foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) или [For Each...Next (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) в коде, их можно преобразовать в цикл [for](/dotnet/csharp/language-reference/keywords/for) с помощью этого рефакторинга кода.

Область применения этого рефакторинга:

- C#

- Visual Basic

### <a name="why-convert"></a>Для чего это нужно

Причины, из-за которых может потребоваться преобразование оператора [foreach](/dotnet/csharp/language-reference/keywords/for) в цикл [for](/dotnet/csharp/language-reference/keywords/foreach-in), включают в себя:

- Вы хотите использовать локальную переменную внутри цикла не только для доступа к элементу.

- Вы [перебираете элементы многомерного массива](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) и вам требуется больший контроль над элементами массива.

### <a name="how-to-use-it"></a>Использование

1. Поместите курсор на ключевое слово `foreach` или `For Each`.

1. Нажмите клавиши **CTRL**+**.** или нажмите значок отвертки ![значок отвертки](../media/screwdriver-icon.png) на полях файла кода.

   ![Меню преобразования в for](media/convert-to-for.png)

1. Выберите **Преобразовать в for**. Также можно выбрать **Просмотр изменений**, чтобы открыть диалоговое окно [Просмотр изменений](../../ide/preview-changes.md), и нажать **Применить**.

1. Так как в данном случае рефакторинг кода порождает новую переменную — счетчик итераций, в правом верхнем углу редактора появится поле **Переименовать**. Если необходимо выбрать другое имя для переменной, введите его и нажмите клавишу **ВВОД** или кнопку **Применить** в поле **Переименовать**. Если вы не хотите изменять имя, нажмите клавишу **ESC** или кнопку **Применить**, чтобы закрыть поле **Переименовать**.

> [!NOTE]
> Код C#, созданный в процессе выполнения рефакторинга, использует явный тип или ключевое слово [var](/dotnet/csharp/language-reference/keywords/var) для этого типа элементов в коллекции. Тип в созданном коде (явный или неявный) зависит от параметров стиля кода, которые находятся в области. Эти конкретные параметры стиля кода задаются на уровне компьютера в разделе **Сервис** > **Параметры** > **Текстовый редактор** > **C#** > **Стиль кода** > **Общие** > **\'предпочтения "var"** или на уровне решения в файле [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types). Если вы измените эти параметры в меню **Параметры**, снова откройте файл кода, чтобы изменения вступили в силу.

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)