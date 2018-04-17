---
title: 'CA2207: Инициализируйте статические поля типа значений встроенными | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5d063cda94451feef28aba9715033234d9adaa1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: инициализируйте статические поля типа значений встроенными средствами
|||  
|-|-|  
|TypeName|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Тип значения объявляет явный статический конструктор.  
  
## <a name="rule-description"></a>Описание правила  
 При объявлении типа значения, к нему применяется инициализация по умолчанию, где все поля типа значения равны нулю, а все поля ссылочного типа присваивается `null` (`Nothing` в Visual Basic). Явный статический конструктор только обязательно выполняется перед конструктором экземпляра или вызова статического члена типа. Таким образом Если тип создается без вызова конструктора экземпляра, статический конструктор не гарантируется для запуска.  
  
 Если все статические данные инициализированный встроенным образом и объявляется явный статический конструктор, компиляторы C# и Visual Basic добавьте `beforefieldinit` флаг к определению класса MSIL. Компиляторы также добавляют закрытый статический конструктор, который содержит статический код инициализации. Этот закрытый статический конструктор обязательно выполняется перед доступны все статические поля типа.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила инициализацию всех статических данных при объявляется и удалите статический конструктор.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1810: инициализируйте статические поля ссылочного типа встроенными средствами](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)