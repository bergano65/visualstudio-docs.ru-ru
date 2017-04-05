---
title: "Стили кода и быстрые действия | Документы Майкрософт"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 25bb9d99-aeff-4053-925d-2177f5e79574
author: BrianPeek
ms.author: brpeek
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: acc01617fffd7465cee01267482112aac5e352fc
ms.lasthandoff: 03/27/2017

---

# <a name="code-styles-and-quick-actions"></a>Стили кода и быстрые действия
Параметры стиля кода можно задать для проектов C# и Visual Basic, открыв окно **Сервис > Параметры**, а затем выбрав **Текстовый редактор > C# / Basic > Стиль кода > Общие**.  Параметры, заданные в этом окне, применяются к локальному компьютеру.  При выборе для каждого из элементов в списке выводится окно предварительного просмотра, как показано ниже.

![Параметры стиля кода](media/code-style-quick-actions-dialog.png)

Для каждого элемента с помощью раскрывающихся списков в каждой строке можно задать **Предпочтения** и **Важность**.  Для важности можно задать значения **Нет**, **Предложение**, **Предупреждение** или **Ошибка**, чтобы система Visual Studio работала соответствующим образом.  Если вы хотите использовать [быстрые действия](quick-actions.md) с этими стилями кода, чтобы автоматически переписать код в предпочитаемом стиле, убедитесь, что для параметра задано значение, отличное от **Нет**, чтобы при использовании непредпочтительных стилей появлялся значок лампочки ![маленький значок лампочки](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall").  Затем эти параметры можно применить, щелкнув значок лампочки или нажав клавиши **CTRL+.**, когда курсор находится на подходящей строке кода.

Параметрами стиля кода для .NET также можно управлять с помощью файла [EditorConfig](editorconfig-code-style-settings-reference.md).  В этом случае параметры, выбранные в окне параметров, будут резервными, а приоритет будет иметь файл EditorConfig.  Этот файл можно использовать для применения и настройки стиля кода для всего репозитория или команды.

# <a name="see-also"></a>См. также
* [Быстрые действия](quick-actions.md)
