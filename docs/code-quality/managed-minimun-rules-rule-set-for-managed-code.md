---
title: Набор правил управляемого минимальные правила для управляемого кода | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6c14af4c569749273b6ed6b73fe48249df3f1ee0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Управляемый минимальные правила набора правил для управляемого кода
Минимальные правила управляемых сосредоточиться на наиболее важные проблемы в коде, включая возможные уязвимости безопасности, сбои приложения и другие важные ошибки логики и проектирования. Следует включать этот набор правил в любой настраиваемый набор правил, создаваемые для проектов.  
  
|Правило|Описание|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Типы, которым принадлежат освобождаемые поля, должны быть высвобождаемыми|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Удаляйте пустые методы завершения|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Следует высвобождать высвобождаемые поля|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Перегрузка оператора равенства на переопределяющем типе ValueType.Equals|
