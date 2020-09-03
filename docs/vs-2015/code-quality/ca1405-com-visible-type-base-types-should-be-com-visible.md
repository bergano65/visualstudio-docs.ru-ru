---
title: 'CA1405: базовые типы видимого COM-типа должны быть видимыми для COM | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 779d3ec1ed520d5d48043f90e7cb6272553012a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535048"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405. Базовые типы, относящиеся к типу, видимому для COM, должны быть видимыми для COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|депендсонфикс|

## <a name="cause"></a>Причина
 Видимый тип модели COM является производным от типа, который не является видимым для COM.

## <a name="rule-description"></a>Описание правила
 Когда видимый тип COM добавляет элементы в новую версию, он должен соблюдать строгие правила, чтобы избежать нарушения работы COM-клиентов, привязанных к текущей версии. Тип, невидимый для COM, предполагает, что он не должен следовать этим правилам управления версиями COM при добавлении новых членов. Однако если видимый тип COM является производным от невидимого типа COM и предоставляет интерфейс класса <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ClassInterfaceType> (значение по умолчанию), все открытые члены базового типа (если они не помечены как невидимые как com, которые могут быть избыточными) доступны для com. Если базовый тип добавляет новые члены в последующей версии, все COM-клиенты, которые привязаны к интерфейсу класса производного типа, могут прерываться. Видимые типы COM должны быть производными только от видимых типов COM, чтобы снизить вероятность нарушения работы клиентов COM.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, сделайте базовые типы видимыми для COM или производным от него типом COM.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>См. также:
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>[Знакомство с интерфейсом класса](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [для взаимодействия с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
