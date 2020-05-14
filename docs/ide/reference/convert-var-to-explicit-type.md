---
title: Рефакторинг кода для замены ключевого слова var явным типом
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 4ec388564e1851402f085f6bbaefba08dbea212c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595778"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Рефакторинг кода для замены ключевого слова var явным типом

Этот рефакторинг кода позволяет заменить ключевое слово [var](/dotnet/csharp/language-reference/keywords/var) в объявлении локальной переменной на явно заданный тип.

Область применения этого рефакторинга:

- C#

## <a name="why-to-use-an-explicit-type"></a>Причины использования явного типа

Ниже приведены некоторые причины объявления переменной с явно заданным типом.

- Улучшение читабельность кода.

- Не нужно инициализировать переменную в объявлении.

Тем не менее ключевое слово [var](/dotnet/csharp/language-reference/keywords/var) нужно использовать, если переменная инициализируется с помощью анонимного типа и вам потребуется доступ к свойствам объекта на более позднем этапе. Дополнительные сведения см. в руководстве по программированию C# [Неявно типизированные локальные переменные](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Использование

1. Поместите курсор на ключевое слово `var`.

1. Нажмите клавиши **CTRL**+ **.** или щелкните значок отвертки ![значок отвертки](../media/screwdriver-icon.png) на полях файла кода.

   ![Меню быстрых действий "Использование явного типа"](media/use-explicit-type.png)

1. Выберите **Использование явного типа**. Также можно выбрать **Просмотр изменений**, чтобы открыть диалоговое окно [Просмотр изменений](../../ide/preview-changes.md), и нажать **Применить**.

## <a name="see-also"></a>См. также раздел

- [Неявно типизированные переменные (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)
