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
ms.openlocfilehash: afd4b758332d9357dc20dd84e726d72da4d2db74
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355193"
---
# <a name="generate-usings-in-visual-studio"></a>Создание директив using в Visual Studio

Область применения этого формирования кода:

- C#

**Что?** Позволяет немедленно добавить необходимые импортированные элементы или [операторы using](/dotnet/csharp/language-reference/keywords/using-statement) скопированного и вставленного кода.

**Когда?** Часто приходится копировать и вставлять код из разных мест проекта или других источников. Это быстрое действие анализирует отсутствующие импортируемые элементы для скопированного и вставленного кода и запрашивает их добавление.

**Зачем?** Автоматическое добавление необходимых импортированных элементов позволяет не копировать нужные операторы `using` вручную.

## <a name="generate-usings-refactoring"></a>Рефакторинг "Создание операторов using"

1. Скопируйте и вставьте код из другого файла, не включая необходимые операторы `using`. Ошибка сопровождается исправлением кода, которое добавляет отсутствующие операторы `using`.

    > [!NOTE] 
    > Эти подсказки нужно включить в разделе **Сервис > Параметры > Текстовый редактор > C# > Дополнительно > Директивы using**.

2. Нажмите клавиши **CTRL**+**.** чтобы открыть меню **Быстрые действия и рефакторинг**. 

    ![Создание директив using](media/generate-using-codefix.png)

3. Выберите **using \<ваша ссылка\>;**, чтобы добавить отсутствующую ссылку.

    ![Результат создания директив using](media/generate-using-result.png)

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)
- [Советы для разработчиков .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
