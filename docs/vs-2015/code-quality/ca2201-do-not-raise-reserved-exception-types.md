---
title: 'CA2201: не вызывайте зарезервированные типы исключений | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseReservedExceptionTypes
- CA2201
helpviewer_keywords:
- CA2201
- DoNotRaiseReservedExceptionTypes
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a550226a5ea1edb3b30e317be6b5682f4c204d52
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667379"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201: не вызывайте зарезервированные типы исключений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseReservedExceptionTypes|
|CheckId|CA2201|
|Категория|Microsoft. Usage|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Метод создает тип исключения, который является слишком общим или зарезервированным средой выполнения.

## <a name="rule-description"></a>Описание правила
 Следующие типы исключений слишком общие для предоставления пользователю достаточной информации:

- <xref:System.Exception?displayProperty=fullName>

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.SystemException?displayProperty=fullName>

  Следующие типы исключений зарезервированы и должны вызываться только средой CLR:

- <xref:System.ExecutionEngineException?displayProperty=fullName>

- <xref:System.IndexOutOfRangeException?displayProperty=fullName>

- <xref:System.NullReferenceException?displayProperty=fullName>

- <xref:System.OutOfMemoryException?displayProperty=fullName>

  **Не вызывайте общие исключения**

  Если вы выдаете общий тип исключения, например <xref:System.Exception> или <xref:System.SystemException> в библиотеке или платформе, он заставляет потребителей перехватывать все исключения, включая неизвестные исключения, которые они не узнают о том, как их обрабатывайте.

  Вместо этого либо вызовите более производный тип, уже существующий в платформе, либо создайте собственный тип, производный от <xref:System.Exception>.

  **Создавать определенные исключения**

  В следующей таблице показаны параметры и исключения, которые следует вызывать при проверке параметра, включая параметр value в методе доступа set свойства.

|Описание параметра|Исключение|
|---------------------------|---------------|
|Ссылка на `null`|<xref:System.ArgumentNullException?displayProperty=fullName>|
|За пределами допустимого диапазона значений (например, индекса для коллекции или списка);|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Недопустимое значение `enum`|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Содержит формат, который не соответствует спецификациям параметров метода (например, строке формата для `ToString(String)`).|<xref:System.FormatException?displayProperty=fullName>|
|В противном случае недопустимо|<xref:System.ArgumentException?displayProperty=fullName>|

 Если операция недопустима для текущего состояния объекта, вызывается <xref:System.InvalidOperationException?displayProperty=fullName>

 При выполнении операции с объектом, который был ликвидирован, <xref:System.ObjectDisposedException?displayProperty=fullName>

 Если операция не поддерживается (например, в переопределенном **потоке. Write** в потоке, открытом для чтения), вызывается исключение <xref:System.NotSupportedException?displayProperty=fullName>

 Если преобразование приведет к переполнению (например, в явной перегрузке оператора приведения), возникает исключение <xref:System.OverflowException?displayProperty=fullName>.

 Во всех остальных случаях рекомендуется создать собственный тип, производный от <xref:System.Exception>, и создать его.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените тип созданного исключения на конкретный тип, который не является одним из зарезервированных типов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="related-rules"></a>Связанные правила
 [CA1031: не перехватывайте типы общих исключений](../code-quality/ca1031-do-not-catch-general-exception-types.md)
