---
title: "CA2201: не вызывайте зарезервированные типы исключений | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotRaiseReservedExceptionTypes"
  - "CA2201"
helpviewer_keywords: 
  - "CA2201"
  - "DoNotRaiseReservedExceptionTypes"
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2201: не вызывайте зарезервированные типы исключений
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Метод создает исключение слишком общего типа или типа, зарезервированного средой выполнения.  
  
## Описание правила  
 Указанные ниже типы исключений являются слишком общими, чтобы предоставлять пользователям исчерпывающую информацию.  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 Указанные ниже типы исключений являются зарезервированными и должны создаваться только средой CLR.  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **Не создавайте общих исключений**  
  
 Создание в библиотеке или платформе исключения общего типа, такого как <xref:System.Exception> или <xref:System.SystemException>, вынуждает объекты\-получатели перехватывать все исключения, в том числе неизвестные, способ обработки которых им не известен.  
  
 Вместо этого следует вызывать исключения производного типа, уже существующего в платформе, или создать собственный тип, производный от <xref:System.Exception>.  
  
 **Создание конкретных исключений**  
  
 В представленной ниже таблице показаны параметры и исключения, которые следует вызывать при проверке параметров, в том числе параметры значения в методе установки свойства:  
  
|Описание параметра|Исключение|  
|------------------------|----------------|  
|Ссылка `null`|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|Выход за пределы диапазона допустимых значений \(например, индекса коллекции или списка\)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|Недопустимое значение `enum`|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|Содержит формат, который не соответствует спецификациям параметров метода \(например, строке формата для метода `ToString(String)`\)|<xref:System.FormatException?displayProperty=fullName>|  
|Другие случаи недопустимых значений|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 Если операция является недопустимой для текущего состояния объекта, создавайте исключение <xref:System.InvalidOperationException?displayProperty=fullName>  
  
 Если операция выполняется для удаленного объекта, создавайте исключение <xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 Если операция не поддерживается \(как, например, переопределенный метод **Stream.Write** в потоке, открытом для чтения\), создавайте исключение <xref:System.NotSupportedException?displayProperty=fullName>  
  
 Если преобразование приводит к переполнению \(как, например, в явной перегрузке оператора приведения\), создавайте исключение <xref:System.OverflowException?displayProperty=fullName>  
  
 В других случаях рассмотрите возможность создания собственного типа, производного от <xref:System.Exception>, и создавайте исключения этого типа.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, замените тип создаваемых исключений на более конкретный тип, не зарезервированный в среде выполнения.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Связанные правила  
 [CA1031: не перехватывайте типы общих исключений](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)