---
title: Параметры стиля кода Visual Studio | Документы Майкрософт
ms.custom: ''
ms.date: 03/10/2017
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 4898a2e4a55f5c11179ae5a00e46c87a44519a7b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="code-style-preferences"></a>Параметры стиля кода

Параметры стиля кода для проектов C# и Visual Basic можно задать, открыв диалоговое окно **Параметры** из меню **Сервис**. Выберите **Текстовый редактор** > **C#** или **Visual Basic** > **Стиль кода** > **Общие**. Параметры, заданные в этом окне, применяются к локальному компьютеру. При выборе для каждого из элементов в списке выводится окно предварительного просмотра, как показано ниже.

![Параметры стиля кода](media/code-style-quick-actions-dialog.png)

Для каждого элемента с помощью раскрывающихся списков в каждой строке можно задать значения для параметров **Предпочтения** и **Серьезность**. Для серьезности можно задать значения **Нет**, **Предложение**, **Предупреждение** или **Ошибка**. Если вы хотите включить [быстрые действия](../ide/quick-actions.md) для стиля кода, убедитесь, что для параметра **Серьезность** задано значение, отличное от **Нет**. Значок лампочки для быстрых действий ![Маленький значок лампочки](media/vs2015_lightbulbsmall.png) будет отображаться при использовании альтернативного стиля. Вы можете выбрать нужный вариант в списке быстрых действий для автоматического повторного создания кода в предпочитаемом стиле.

Параметрами стиля кода для .NET также можно управлять с помощью файла [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). В этом случае параметры в файле EditorConfig имеют приоритет над параметрами, выбранными в диалоговом окне **Параметры**. Файл EditorConfig можно использовать для применения и настройки стиля кода для всего репозитория или проекта.

### <a name="see-also"></a>См. также

[Быстрые действия](../ide/quick-actions.md)  
[Параметры соглашений о написании кода .NET в EditorConfig](../ide/editorconfig-code-style-settings-reference.md)