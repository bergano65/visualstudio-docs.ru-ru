---
title: Как выполнить  Создание рабочего элемента для дефекта управляемого кода
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e2e55ddf51e0c81f57c504e398c23c8e1d3f721a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934800"
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Как выполнить  Создание рабочего элемента для дефекта управляемого кода

Можно использовать функции отслеживания рабочих элементов для журнала рабочего элемента из Visual Studio. Чтобы использовать эту функцию, проект должен быть частью в проект Azure DevOps в [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)].

## <a name="to-create-a-work-item-for-managed-code-defect"></a>Для создания рабочего элемента для дефекта управляемого кода

1. В **анализа кода** окно, выберите предупреждение.

2. Выберите **действия**, затем выберите **создать рабочий элемент** и выберите тип создаваемого рабочего элемента.

     Для указания информации о дефектах, создается новый рабочий элемент.

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Для создания рабочего элемента для нескольких дефектов управляемого кода

1. В **список ошибок**, выберите несколько предупреждений и щелкните правой кнопкой мыши предупреждения.

2. Пункты **создать рабочий элемент** и выберите тип создаваемого рабочего элемента.

     Отдельный рабочий элемент создается для всех выбранных предупреждений следует указать сведения об ошибках.