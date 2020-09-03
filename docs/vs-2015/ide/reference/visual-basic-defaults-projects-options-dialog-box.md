---
title: Страница "Параметры Visual Basic по умолчанию", папка "Проекты", диалоговое окно "Параметры" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f08cc817fab6e81ae1160462c9b6d1221ca41160
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657877"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>Страница "Параметры Visual Basic по умолчанию", папка "Проекты", диалоговое окно "Параметры"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает значения по умолчанию для параметров проекта Visual Basic. При создании проекта указанные операторы option добавляются в заголовок проекта в редакторе кода. Эти параметры применяются ко всем проектам Visual Basic.

 Чтобы открыть это диалоговое окно, в меню **Сервис** выберите **Параметры**, разверните папку **Проекты и решения** и выберите **Параметры Visual Basic по умолчанию**.

 **Option Explicit** Задает значение компилятора по умолчанию, чтобы явно объявлять переменные были обязательными. По умолчанию **Option Explicit** имеет значение **On**. Дополнительные сведения см. в описании [/optionexplicit](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7).

 **Optioned** Задает значение по умолчанию компилятора, чтобы явное сужающие преобразования требовались, а позднее связывание не разрешено. По умолчанию **Option Strict** имеет значение **Off**. Дополнительные сведения см. в описании [/optionstrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da).

 **Параметр Compare** Задает компилятор по умолчанию для сравнений строк: двоичный (с учетом регистра) или текст (без учета регистра). По умолчанию **параметр Compare** имеет значение **binary**. Дополнительные сведения см. в описании [/optioncompare](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4).

 **Параметр Infer** Задает значение по умолчанию компилятора для определения локального типа. По умолчанию **Option Infer** имеет значение **On** для вновь созданных проектов и **Off** для проектов, перенесенных из более ранних версий Visual Basic. Дополнительные сведения см. в описании [/optioninfer](https://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed).

## <a name="see-also"></a>См. также:
 [Решения и проекты](../../ide/solutions-and-projects-in-visual-studio.md)
