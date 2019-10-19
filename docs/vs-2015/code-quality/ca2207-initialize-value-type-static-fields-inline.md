---
title: 'CA2207: инициализируйте статические поля типа значения во встроенном | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a2b3c1faf4ecf3ecf79a3c78d0ded106b88345ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609367"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: инициализируйте статические поля типа значений встроенными средствами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип значения объявляет явный статический конструктор.

## <a name="rule-description"></a>Описание правила
 При объявлении типа значения он проходит инициализацию по умолчанию, где все поля типа значения имеют нулевое значение, а всем полям ссылочного типа присваивается значение `null` (`Nothing` в Visual Basic). Явный статический конструктор гарантированно выполняется только перед вызовом конструктора экземпляра или статического члена типа. Таким образом, если тип создается без вызова конструктора экземпляра, выполнение статического конструктора не гарантируется.

 Если все статические данные инициализируются встроенным образом и не объявлен явный статический конструктор, компиляторы C# и Visual Basic добавляют флаг `beforefieldinit` в определение класса MSIL. Компиляторы также добавляют закрытый статический конструктор, который содержит статический код инициализации. Этот закрытый статический конструктор гарантированно выполняется перед обращением к любым статическим полям типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, инициализируйте все статические данные при объявлении и удалите статический конструктор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="related-rules"></a>Связанные правила
 [CA1810: инициализируйте статические поля ссылочного типа встроенными средствами](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)
