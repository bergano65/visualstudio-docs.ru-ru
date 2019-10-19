---
title: 'CA2208: правильное создание экземпляров исключений аргументов | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5b5e1525d1ee706f9cd46a58c022763d2ed234bf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662686"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: правильно создавайте экземпляры аргументов исключений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Возможные причины включают в себя следующие ситуации.

- Выполняется вызов конструктора по умолчанию (без параметров) для типа исключения, который является или является производным от [System. ArgumentException] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

- Неверный строковый аргумент передан в параметризованный конструктор типа исключения, который является или является производным от [System. ArgumentException.] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Описание правила
 Вместо вызова конструктора по умолчанию вызовите одну из перегрузок конструктора, которая позволяет предоставить более осмысленное сообщение об исключении. Сообщение об исключении должно ориентироваться на разработчика и ясно объяснить состояние ошибки, а также как исправить или избежать исключения.

 Сигнатуры одного и двух конструкторов строк <xref:System.ArgumentException> и их производных типов не согласуются с параметрами `message` и `paramName`. Убедитесь, что эти конструкторы вызываются с правильными строковыми аргументами. Ниже приведены сигнатуры.

 <xref:System.ArgumentException> (строка `message`)

 <xref:System.ArgumentException> (строка `message`, строка `paramName`)

 <xref:System.ArgumentNullException> (строка `paramName`)

 <xref:System.ArgumentNullException> (строка `paramName`, строка `message`)

 <xref:System.ArgumentOutOfRangeException> (строка `paramName`)

 <xref:System.ArgumentOutOfRangeException> (строка `paramName`, строка `message`)

 <xref:System.DuplicateWaitObjectException> (строка `parameterName`)

 <xref:System.DuplicateWaitObjectException> (строка `parameterName`, строка `message`)

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите конструктор, принимающий сообщение, имя параметра или оба значения, и убедитесь, что аргументы являются верными для вызова типа <xref:System.ArgumentException>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, только если параметризованный конструктор вызывается с правильными строковыми аргументами.

## <a name="example"></a>Пример
 В следующем примере показан конструктор, который неправильно создает экземпляр типа ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Пример
 В следующем примере описанное выше нарушение устраняется путем переключения аргументов конструктора.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]
