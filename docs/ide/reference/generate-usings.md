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
ms.openlocfilehash: 0ce1b620a6d8aba7e4aea767745891dff6d9f869
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59537508"
---
# <a name="generate-usings-in-visual-studio"></a>Создание директив using в Visual Studio

Область применения этого формирования кода:

- C#

**Что?** Позволяет немедленно добавить необходимые импортированные элементы или [операторы using](/dotnet/csharp/language-reference/keywords/using-statement) скопированного и вставленного кода.

**Когда?** Часто приходится копировать существующий код из разных частей проекта или других источников и вставлять его в новый код. Это быстрое действие находит отсутствующие импортируемые элементы и операторы для скопированного и вставленного кода и запрашивает их добавление.

**Зачем?** Так как это быстрое действие автоматически добавляет необходимые импортируемые элементы, вам не нужно вручную копировать операторы `using`, которые должны присутствовать в коде.

## <a name="generate-usings-refactoring"></a>Рефакторинг "Создание операторов using"

1. Скопируйте код в одном файле и вставьте его в другой, не включая необходимые операторы `using`. Итоговая ошибка сопровождается исправлением кода, которое добавляет отсутствующие операторы `using`.

    > [!NOTE] 
    > Это предложения нужно включить в разделе **Сервис > Параметры > Текстовый редактор > C# > Дополнительно > Директивы using**.

2. Нажмите клавиши CTRL+. чтобы открыть меню **Быстрые действия и рефакторинг**.

    ![Создание директив using](media/generate-using-codefix.png)

3. Выберите **using \<ваша ссылка\>;**, чтобы добавить отсутствующую ссылку.

    ![Результат создания директив using](media/generate-using-result.png)

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)
- [Советы для разработчиков .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
