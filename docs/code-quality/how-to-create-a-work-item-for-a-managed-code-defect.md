---
title: Практическое руководство. Создание рабочего элемента для дефекта управляемого кода
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b251970bfd57b31842e1573e2e156e11a517c81a
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279480"
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Практическое руководство. Создание рабочего элемента для дефекта управляемого кода

Можно использовать функции отслеживания рабочих элементов для журнала рабочего элемента из Visual Studio. Чтобы использовать эту функцию, проект должен быть частью в проект Azure DevOps в [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

## <a name="to-create-a-work-item-for-managed-code-defect"></a>Для создания рабочего элемента для дефекта управляемого кода

1. В **анализа кода** окно, выберите предупреждение.

2. Выберите **действия**, затем выберите **создать рабочий элемент** и выберите тип создаваемого рабочего элемента.

     Для указания информации о дефектах, создается новый рабочий элемент.

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Для создания рабочего элемента для нескольких дефектов управляемого кода

1. В **список ошибок**, выберите несколько предупреждений и щелкните правой кнопкой мыши предупреждения.

2. Пункты **создать рабочий элемент** и выберите тип создаваемого рабочего элемента.

     Отдельный рабочий элемент создается для всех выбранных предупреждений следует указать сведения об ошибках.