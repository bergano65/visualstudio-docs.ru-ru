---
title: 'CA1811: Не используйте Невызываемый закрытый код | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d9015fe8b7384046b621cd11600528cd76a97c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: не используйте невызываемый закрытый код
|||  
|-|-|  
|TypeName|AvoidUncalledPrivateCode|  
|CheckId|CA1811|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 (На уровне сборки) член закрытым или внутренним ни объектами сборки, не используется средой CLR и не вызывается делегат. Это правило не проверяются следующие члены:  
  
-   Явные члены интерфейса.  
  
-   Статические конструкторы.  
  
-   Конструкторы сериализации.  
  
-   Методы, помеченные <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.  
  
-   Элементы, которые являются переопределениями.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило можно отчетов ложных положительных результатов в случае точки входа, в настоящее время не определены логикой правила. Кроме того компилятор может вставить noncallable кода в сборку.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите noncallable код или добавьте код, который вызывает ее.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Его можно безопасно подавить предупреждение из этого правила.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1812: не создавайте внутренние классы без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)