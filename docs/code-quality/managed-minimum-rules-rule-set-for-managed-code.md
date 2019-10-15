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
ms.openlocfilehash: bc3d0376e0f3af186802fa566e1618ae7ed89a78
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305603"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Набор правил "Минимальные правила для управляемого кода"

Управляемые минимальные правила касаются наиболее важных проблем в коде, включая потенциальные бреши в системе безопасности, сбои приложений и другие важные ошибки логики и разработки. Включите это правило в набор настраиваемых правил, создаваемых для проектов.

|Правило|Описание|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|
|[CA1821](../code-quality/ca1821.md)|Удалите пустые методы завершения|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Следует высвобождать высвобождаемые поля|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Перегрузка оператора равенства при переопределении `ValueType.Equals`|
