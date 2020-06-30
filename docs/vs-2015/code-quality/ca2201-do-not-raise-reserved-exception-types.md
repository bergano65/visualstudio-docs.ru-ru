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
ms.openlocfilehash: 9533a597a33deaed17ff2a73d56ef306ea7b5613
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546345"
---
# <a name="ca2201-do-not-raise-reserved-exception-types"></a>CA2201. Не порождайте исключения зарезервированных типов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
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

  Если выдается общий тип исключения, например, <xref:System.Exception> или <xref:System.SystemException> в библиотеке или платформе, он заставляет потребителей перехватывать все исключения, включая неизвестные исключения, которые они не узнают о том, как обрабатывались.

  Вместо этого либо вызовите более производный тип, уже существующий в платформе, либо создайте собственный тип, производный от <xref:System.Exception> .

  **Создавать определенные исключения**

  В следующей таблице показаны параметры и исключения, которые следует вызывать при проверке параметра, включая параметр value в методе доступа set свойства.

|Описание параметра|Исключение|
|---------------------------|---------------|
|`null`IsReference|<xref:System.ArgumentNullException?displayProperty=fullName>|
|За пределами допустимого диапазона значений (например, индекса для коллекции или списка);|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|
|Недопустимое `enum` значение|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|
|Содержит формат, который не соответствует спецификациям параметров метода (например, строке форматирования для `ToString(String)` ).|<xref:System.FormatException?displayProperty=fullName>|
|В противном случае недопустимо|<xref:System.ArgumentException?displayProperty=fullName>|

 Если операция недопустима для текущего состояния выдачи объекта<xref:System.InvalidOperationException?displayProperty=fullName>

 При выполнении операции с объектом, для которого было ликвидировано исключение<xref:System.ObjectDisposedException?displayProperty=fullName>

 Если операция не поддерживается (например, в переопределенном **потоке. Write** в потоке, открытом для чтения), выдается исключение<xref:System.NotSupportedException?displayProperty=fullName>

 Если преобразование приведет к переполнению (например, в явной перегрузке оператора приведения), выдается исключение<xref:System.OverflowException?displayProperty=fullName>

 Во всех остальных случаях рекомендуется создать собственный тип, производный от, <xref:System.Exception> и создать его.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените тип созданного исключения на конкретный тип, который не является одним из зарезервированных типов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="related-rules"></a>Связанные правила
 [CA1031. Не перехватывайте типы общих исключений](../code-quality/ca1031-do-not-catch-general-exception-types.md)
