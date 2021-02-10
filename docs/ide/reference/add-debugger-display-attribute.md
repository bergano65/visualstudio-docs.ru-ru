---
title: Добавление атрибута DebuggerDisplay
description: Сведения о том, как добавить атрибут DebuggerDisplay для управления способом, который используется окном переменной отладчика для отображения объекта, свойства или поля.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2166f7876909f62d9d16a2a6d5ec126d4544193e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956728"
---
# <a name="add-debuggerdisplay-attribute"></a>Добавление атрибута DebuggerDisplay

Область применения этого формирования кода:

- C#

**Что?** [Атрибут DebuggerDisplay](../../debugger/using-the-debuggerdisplay-attribute.md) управляет тем, как объект, свойство или поле отображаются в окнах переменных отладчика.

**Когда?** Вам нужно [закрепить свойства](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips) в отладчике программным способом в коде.

**Зачем?** Закрепление свойств позволяет быстро проверять объекты по их свойствам, перенося указанное свойство в верхнюю часть списка свойств объекта в отладчике. 

## <a name="how-to"></a>Практические советы

1. Поместите курсор на тип, делегат, свойство или поле. 

2. Нажмите клавиши **CTRL**+ **.** чтобы активировать меню **Быстрые действия и рефакторинг** и выбрать **Добавить атрибут DebuggerDisplay**.

    ![Создание операторов сравнения](media/add-debugger-display-attribute.png)

3. Атрибут DebuggerDisplay будет добавлен вместе с методом auto, который возвращает значение ToString () по умолчанию. 

## <a name="see-also"></a>См. также

- [Создание кода](../code-generation-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)