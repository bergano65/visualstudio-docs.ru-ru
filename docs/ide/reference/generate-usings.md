---
title: Создание директив using
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
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 903b160bac0e8096062e09fd78ff4c92c46cf8ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094320"
---
# <a name="add-missing-usings-in-visual-studio"></a>Добавление пропущенных директив using в Visual Studio

Область применения этого формирования кода:

- C#

- Visual Basic

**Что?** Позволяет немедленно добавить необходимые импортированные элементы или [директива using](/dotnet/csharp/language-reference/keywords/using-directive) для скопированного и вставленного кода.

**Когда?** Часто приходится копировать существующий код из разных частей проекта или других источников и вставлять его в новый код. Это быстрое действие находит отсутствующие импортируемые элементы и директивы для скопированного и вставленного кода и запрашивает их добавление. Это исправление кода также может добавлять ссылки из проекта в проект.

**Зачем?** Так как это быстрое действие автоматически добавляет необходимые импортируемые элементы, вам не нужно вручную копировать директивы `using`, которые должны присутствовать в коде.

## <a name="add-missing-usings-refactoring"></a>Добавление пропущенного рефакторинга операторов using

1. Скопируйте код в одном файле и вставьте его в другой, не включая необходимые директивы `using`. Итоговая ошибка сопровождается исправлением кода, которое добавляет отсутствующие директивы `using`.

    > [!NOTE]
    > Это предложения нужно включить в разделе **Сервис > Параметры > Текстовый редактор > C# > Дополнительно > Директивы using**.

2. Нажмите клавиши CTRL+. чтобы открыть меню **Быстрые действия и рефакторинг**.

    ![Создание директив using](media/generate-using-codefix.png)

3. Выберите **using \<your reference\>;** , чтобы добавить отсутствующую ссылку.

    ![Результат создания директив using](media/generate-using-result.png)

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)
- [Советы для разработчиков .NET](../csharp-developer-productivity.md)
