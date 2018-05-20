---
title: Рефакторинг кода для преобразования цикла for в оператор foreach
ms.date: 05/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 34758473bcbee8ccad7d9dff9df2f1478ca1202c
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2018
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Рефакторинг кода для преобразования цикла for в оператор foreach и наоборот

Область применения этих операций рефакторинга:

- C#

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Преобразование цикла for в оператор foreach

Если у вас есть цикл [for](/dotnet/csharp/language-reference/keywords/for) в коде, можно использовать этот рефакторинг кода для преобразования цикла в оператор [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

### <a name="why-convert"></a>Для чего это нужно

Причины, из-за которых может потребоваться преобразование цикла [for](/dotnet/csharp/language-reference/keywords/for) в оператор [foreach](/dotnet/csharp/language-reference/keywords/foreach-in), включают в себя:

- Вы используете переменную — счетчик итераций внутри цикла только в качестве индекса для доступа к элементу.

- Вы хотите упростить код и уменьшить вероятность возникновения логических ошибок в инициализаторе, условиях и операторах итераций.

### <a name="how-to-use-it"></a>Использование

1. Поместите курсор на первую строку цикла `for`.

1. Нажмите клавиши **CTRL**+**.** или нажмите значок отвертки ![значок отвертки](../media/screwdriver-icon.png) на полях файла кода.

   ![Меню преобразования в foreach](media/convert-to-foreach.png)

1. Выберите **Преобразовать в foreach**. Также можно выбрать **Просмотр изменений**, чтобы открыть диалоговое окно [Просмотр изменений](../../ide/preview-changes.md), и нажать **Применить**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Преобразование оператора foreach в цикл for

Если у вас есть оператор [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) в коде, можно использовать этот рефакторинг кода для преобразования оператора в цикл [for](/dotnet/csharp/language-reference/keywords/for).

### <a name="why-convert"></a>Для чего это нужно

Причины, из-за которых может потребоваться преобразование оператора [foreach](/dotnet/csharp/language-reference/keywords/for) в цикл [for](/dotnet/csharp/language-reference/keywords/foreach-in), включают в себя:

- Вы хотите использовать переменную — счетчик итераций внутри цикла не только для доступа к элементу.

- Вы [перебираете элементы многомерного массива](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) и вам требуется больший контроль над элементами массива.

### <a name="how-to-use-it"></a>Использование

1. Поместите курсор на первую строку оператора `foreach`.

1. Нажмите клавиши **CTRL**+**.** или нажмите значок отвертки ![значок отвертки](../media/screwdriver-icon.png) на полях файла кода.

   ![Меню преобразования в for](media/convert-to-for.png)

1. Выберите **Преобразовать в for**. Также можно выбрать **Просмотр изменений**, чтобы открыть диалоговое окно [Просмотр изменений](../../ide/preview-changes.md), и нажать **Применить**.

1. Так как в данном случае рефакторинг кода порождает новую переменную — счетчик итераций, в правом верхнем углу редактора появится поле **Переименовать**. Если необходимо выбрать другое имя для переменной, введите его и нажмите клавишу **ВВОД** или кнопку **Применить** в поле **Переименовать**. Если вы не хотите изменять имя, нажмите клавишу **ESC** или кнопку **Применить**, чтобы закрыть поле **Переименовать**.

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)