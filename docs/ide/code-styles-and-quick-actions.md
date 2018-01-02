---
title: "Параметры стиля кода Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.openlocfilehash: 24470f4fdb1a75d6ebd2743b2ade72e6195842b4
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2017
---
# <a name="code-style-preferences"></a>Параметры стиля кода

Параметры стиля кода для проектов C# и Visual Basic можно задать, открыв диалоговое окно **Параметры** из меню **Сервис**. Выберите **Текстовый редактор**, **C#** или **Basic**, **Стиль кода**, **Общие**. Параметры, заданные в этом окне, применяются к локальному компьютеру. При выборе для каждого из элементов в списке выводится окно предварительного просмотра, как показано ниже.

![Параметры стиля кода](media/code-style-quick-actions-dialog.png)

Для каждого элемента с помощью раскрывающихся списков в каждой строке можно задать **Предпочтения** и **Важность**. Для важности можно задать значения **Нет**, **Предложение**, **Предупреждение** или **Ошибка**, чтобы система Visual Studio работала соответствующим образом. Если вы хотите использовать [быстрые действия](quick-actions.md) с этими стилями кода, чтобы автоматически переписать код в предпочитаемом стиле, убедитесь, что для параметра задано значение, отличное от **Нет**, чтобы при использовании непредпочтительных стилей появлялся значок лампочки ![маленький значок лампочки](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall"). Затем эти параметры можно применить, щелкнув значок лампочки или нажав клавиши **CTRL+.**, когда курсор находится на подходящей строке кода.

Параметрами стиля кода для .NET также можно управлять с помощью файла [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). В этом случае параметры в файле EditorConfig имеют приоритет над параметрами, выбранными в диалоговом окне **Параметры**. Файл EditorConfig можно использовать для применения и настройки стиля кода для всего репозитория или проекта.

## <a name="see-also"></a>См. также

[Быстрые действия](quick-actions.md)  
[Параметры соглашений о написании кода .NET в EditorConfig](../ide/editorconfig-code-style-settings-reference.md)