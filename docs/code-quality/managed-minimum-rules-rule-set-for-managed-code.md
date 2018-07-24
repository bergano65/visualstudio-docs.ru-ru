---
title: Управляемые минимальные правила набора правил для управляемого кода
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: bf05f4787cbd393173380be8123657abeddc0cd5
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204535"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Управляемые минимальные правила набора правил для управляемого кода

Правила управляемого минимум сосредоточиться на наиболее важными проблемами в коде, включая возможные уязвимости безопасности, сбои приложения и другие важные ошибки логики и проектирования. Этот набор правил включите во все пользовательские наборы правил, создаваемые для проектов.

|Правило|Описание:|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Удалите пустые завершающие методы|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Следует высвобождать высвобождаемые поля|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Перегрузка оператора равенства на переопределяющем типе ValueType.Equals|
