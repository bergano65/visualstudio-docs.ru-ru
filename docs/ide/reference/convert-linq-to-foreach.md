---
title: Рефакторинг кода для преобразования запроса LINQ в оператор foreach
description: Преобразование любого запроса LINQ, написанного в синтаксисе запроса, в инструкцию foreach.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6e1b24cb8406ff29659eb79d1d9fa856db628b89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094091"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Рефакторинг кода для преобразования запроса LINQ в оператор foreach

Этот рефакторинг кода позволяет преобразовать [синтаксис запроса LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) в оператор [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Область применения этого рефакторинга:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Использование

1. Выберите весь запрос LINQ начиная с `from`.

   > [!NOTE]
   > Этот рефакторинг кода позволяет преобразовывать только запросы LINQ, выраженные с помощью синтаксиса запроса, а не синтаксиса метода.

1. Нажмите клавиши **CTRL**+ **.** или щелкните значок отвертки ![значок отвертки](../media/screwdriver-icon.png) на полях файла кода.

   ![Преобразование запроса LINQ в foreach через меню быстрых действий](media/convert-linq-to-foreach.png)

1. Выберите **Преобразовать в foreach**. Также можно выбрать **Просмотр изменений**, чтобы открыть диалоговое окно [Просмотр изменений](../../ide/preview-changes.md), и нажать **Применить**.

> [!NOTE]
> Код C#, созданный в процессе выполнения рефакторинга, использует явный тип или ключевое слово [var](/dotnet/csharp/language-reference/keywords/var) для переменной итерации цикла `foreach`. Тип в созданном коде (явный или неявный) зависит от параметров стиля кода, которые находятся в области. Эти конкретные параметры стиля кода задаются на уровне компьютера в разделе **Сервис** > **Параметры** > **Текстовый редактор** > **C#**  > **Стиль кода** > **Общие** >  **\'предпочтения "var"** или на уровне решения в файле [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types). Если вы измените эти параметры в меню **Параметры**, снова откройте файл кода, чтобы изменения вступили в силу.

## <a name="see-also"></a>См. также раздел

- [LINQ](/dotnet/standard/using-linq)
- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)
