---
title: Набор правил "Минимальные правила для управляемого кода"
ms.date: 11/04/2016
description: Сведения о наборе правил "Управляемые минимальные правила" в Visual Studio, которые нацелены на безопасность, надежность и другие критические проблемы. См. Описание правила.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 8711fd0a265618a5aaf4f84edcf7dd2b081b16a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859818"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Набор правил "Минимальные правила для управляемого кода"

Управляемые минимальные правила касаются наиболее важных проблем в коде, включая потенциальные бреши в системе безопасности, сбои приложений и другие важные ошибки логики и разработки. Включите это правило в набор настраиваемых правил, создаваемых для проектов.

|Правило|Описание|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Удалите пустые методы завершения|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Следует высвобождать высвобождаемые поля|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Перегрузка оператора равна при переопределении `ValueType.Equals`|
