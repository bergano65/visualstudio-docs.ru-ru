---
title: 'CA1810: Ссылку инициализируйте статические поля типа встроенными | Документация Майкрософт'
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
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e4d7ffbe4fc821ffd70b0bb299b2a4738d63873b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862688"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810: инициализируйте статические поля ссылочного типа встроенными средствами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Ссылочный тип объявляет явный статический конструктор.

## <a name="rule-description"></a>Описание правила
 Если в типе объявляется явный статический конструктор, компилятор JIT добавляет проверку в каждый статический метод и конструктор экземпляров этого типа, чтобы убедиться, что статический конструктор уже вызывался ранее. Статическая инициализация выполняется при доступе к статическому члену, или при создании экземпляра типа. Тем не менее статическая инициализация не выполняется, если объявить переменную типа, но его не следует использовать, что может быть важно в том случае, если инициализация изменения глобального состояния.

 При всех статических данных является встроенным инициализированный и явный статический конструктор не объявлен, компиляторы Microsoft промежуточного языка MSIL добавляют `beforefieldinit` флаг и неявный статический конструктор, который инициализирует статические данные, к типу MSIL Определение. Когда JIT-компилятор встречает `beforefieldinit` флаг, в большинстве случаев проверки статических конструкторов не добавляются. Статическая инициализация будет гарантированно выполнена прежде, чем к статическим полям осуществляется, но не перед вызывается статический конструктор, метод или экземпляр. Обратите внимание, что статическая инициализация может произойти в любое время после объявления переменной типа.

 Проверки статических конструкторов могут привести к снижению производительности. Часто статический конструктор используется только для инициализации статических полей, в которых необходимо только убедиться в том статическая инициализация происходит до первого обращения статического поля. `beforefieldinit` Поведение подходит для этих и большинства других типов. Он не только может использоваться, когда статическая инициализация влияет на глобальное состояние и одно из следующих условий верно:

-   Воздействие на глобальное состояние ресурсоемких и не является обязательным, если тип не используется.

-   Изменение глобального состояния может осуществляться без доступа к любой статические поля типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, выполните инициализацию всех статических данных при их объявлении и удалите статический конструктор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить предупреждение из этого правила, если производительность не имеет значения; или если изменения глобального состояния, вызванные статическая инициализация дороги или необходимо гарантировать должно происходить перед вызывается статический метод типа или создается экземпляр типа.

## <a name="example"></a>Пример
 В следующем примере показано типом, `StaticConstructor`, нарушает правило и тип `NoStaticConstructor`, который заменяет статический конструктор на встроенную инициализацию в соответствии с правилом.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 Обратите внимание, добавление `beforefieldinit` флагом в определении MSIL для `NoStaticConstructor` класса.

 **открытый .class auto ansi StaticConstructor** **расширяет [mscorlib]System.Object**
 **{**
 **} / / end класса StaticConstructor** 
 **.class открытый автоматически ansi beforefieldinit NoStaticConstructor** **расширяет [mscorlib]System.Object**
 **{** 
 **} / / end класса NoStaticConstructor**
## <a name="related-rules"></a>Связанные правила
 [CA2207: инициализируйте статические поля типа значений встроенными средствами](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)



