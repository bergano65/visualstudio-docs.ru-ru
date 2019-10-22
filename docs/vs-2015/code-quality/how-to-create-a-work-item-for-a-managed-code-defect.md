---
title: Как создать рабочий элемент для ошибки управляемого кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
ms.assetid: 46ddfd57-af4a-4c1d-bd00-8e6328f321f0
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8a3e9277ca29a20d817b04bf06cde120c0f073d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655135"
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>Практическое руководство. Создание рабочего элемента для дефекта управляемого кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Функцию отслеживания рабочих элементов можно использовать для записи в журнал рабочего элемента из [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. Чтобы использовать эту функцию, проект должен быть частью командного проекта в [!INCLUDE[esprfound](../includes/esprfound-md.md)].

### <a name="to-create-a-work-item-for-managed-code-defect"></a>Создание рабочего элемента для ошибки управляемого кода

1. В окне **анализ кода** выберите предупреждение.

2. Выберите **действия**, затем выберите **создать рабочий элемент** и выберите тип создаваемого рабочего элемента.

     Для указания сведений об ошибках создается новый рабочий элемент.

### <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>Создание рабочего элемента для нескольких дефектов управляемого кода

1. В **Список ошибок**выберите несколько предупреждений, а затем щелкните предупреждения правой кнопкой мыши.

2. Наведите указатель мыши на пункт **создать рабочий элемент** и выберите тип создаваемого рабочего элемента.

     Для всех выбранных предупреждений создается один рабочий элемент для указания сведений об ошибке.
