---
title: 'CA2207: Инициализируйте статические поля типа значений встроенными | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d2833e14c941ae4d2ac6c16f8f5abf625f430de9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890605"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: инициализируйте статические поля типа значений встроенными средствами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип значения объявляет явный статический конструктор.

## <a name="rule-description"></a>Описание правила
 При объявлении типа значения, она подвергается инициализация по умолчанию, где все поля типа значения присваивается нулевое значение, а все поля ссылочного типа присваивается `null` (`Nothing` в Visual Basic). Явный статический конструктор гарантируется только до выполнения конструктора экземпляра или вызове статического члена типа. Таким образом Если тип создается без вызова конструктора экземпляра, статическом конструкторе не гарантируется для запуска.

 Если все статические данные инициализированный встроенные и объявляется явный статический конструктор, компиляторы C# и Visual Basic добавьте `beforefieldinit` флаг к определению класса MSIL. Компиляторы также добавить частный статический конструктор, который содержит статический код инициализации. Этот закрытый статический конструктор обязательно выполняется прежде, чем любые статические поля типа осуществляется.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила инициализацию всех статических данных, если он объявлен и удалите статический конструктор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="related-rules"></a>Связанные правила
 [CA1810: инициализируйте статические поля ссылочного типа встроенными средствами](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)



