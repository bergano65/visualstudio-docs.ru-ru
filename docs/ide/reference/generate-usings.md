---
title: Создание директив using
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: d971bcdaca4efdf587c7e441f1b0b28d21388dee
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416481"
---
# <a name="add-missing-usings-in-visual-studio"></a>Добавление пропущенных директив using в Visual Studio

Область применения этого формирования кода:

- C#

**Что?** Позволяет немедленно добавить необходимые импортированные элементы или [операторы using](/dotnet/csharp/language-reference/keywords/using-statement) скопированного и вставленного кода.

**Когда?** Часто приходится копировать существующий код из разных частей проекта или других источников и вставлять его в новый код. Это быстрое действие находит отсутствующие импортируемые элементы и операторы для скопированного и вставленного кода и запрашивает их добавление.

**Зачем?** Так как это быстрое действие автоматически добавляет необходимые импортируемые элементы, вам не нужно вручную копировать операторы `using`, которые должны присутствовать в коде.

## <a name="add-missing-usings-refactoring"></a>Добавление пропущенного рефакторинга операторов using

1. Скопируйте код в одном файле и вставьте его в другой, не включая необходимые операторы `using`. Итоговая ошибка сопровождается исправлением кода, которое добавляет отсутствующие операторы `using`.

    > [!NOTE]
    > Это предложения нужно включить в разделе **Сервис > Параметры > Текстовый редактор > C# > Дополнительно > Директивы using**.

2. Нажмите клавиши CTRL+. чтобы открыть меню **Быстрые действия и рефакторинг**.

    ![Создание директив using](media/generate-using-codefix.png)

3. Выберите **using \<ваша ссылка\>;** , чтобы добавить отсутствующую ссылку.

    ![Результат создания директив using](media/generate-using-result.png)

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)
- [Советы для разработчиков .NET](../csharp-developer-productivity.md)
