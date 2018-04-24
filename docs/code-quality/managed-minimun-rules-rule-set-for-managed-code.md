---
title: Управляемый минимальные правила набора правил для управляемого кода
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2ec566fb45b68505849639af00f85bbe81aa6f16
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Управляемый минимальные правила набора правил для управляемого кода
Минимальные правила управляемых сосредоточиться на наиболее важные проблемы в коде, включая возможные уязвимости безопасности, сбои приложения и другие важные ошибки логики и проектирования. Следует включать этот набор правил в любой настраиваемый набор правил, создаваемые для проектов.

|Правило|Описание|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Типы, которым принадлежат освобождаемые поля, должны быть высвобождаемыми|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Удаляйте пустые методы завершения|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Следует высвобождать высвобождаемые поля|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Перегрузка оператора равенства на переопределяющем типе ValueType.Equals|
