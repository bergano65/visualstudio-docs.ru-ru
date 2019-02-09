---
title: Набор правил "Минимальные правила для управляемого кода"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: eb9078050b42998bb88ad71580ecd506b9049f86
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930211"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Набор правил "Минимальные правила для управляемого кода"

Правила управляемого минимум сосредоточиться на наиболее важными проблемами в коде, включая возможные уязвимости безопасности, сбои приложения и другие важные ошибки логики и проектирования. Этот набор правил включите во все пользовательские наборы правил, создаваемые для проектов.

|Правило|Описание:|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Удалите пустые методы завершения|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Следует высвобождать высвобождаемые поля|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Перегрузите оператор равенства на переопределяющем типе ValueType.Equals|
