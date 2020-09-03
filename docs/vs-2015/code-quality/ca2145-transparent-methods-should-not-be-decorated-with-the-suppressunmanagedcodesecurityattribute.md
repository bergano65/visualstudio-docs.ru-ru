---
title: 'CA2145: прозрачные методы не должны оформляться с атрибутом SuppressUnmanagedCodeSecurityAttribute | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d5eb16130aef42abcf9fddf533d0253864a75114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546410"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145. Прозрачные методы не должны быть отмечены атрибутом SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|транспарентмесодсшаулднотусесуппрессунманажедкодесекурити|
|CheckId|CA2145|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный метод, метод, помеченный <xref:System.Security.SecuritySafeCriticalAttribute> методом, или тип, содержащий метод, помечены <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибутом.

## <a name="rule-description"></a>Описание правила
 Методы, отмеченные <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> атрибутом, имеют неявное требование LinkDemand, накладываемое любым методом, который его вызывает. Для этой проверки LinkDemand требуется, чтобы вызывающий код был критическим с точки зрения безопасности. Пометка метода, использующего SuppressUnmanagedCodeSecurity с <xref:System.Security.SecurityCriticalAttribute> атрибутом, делает это требование более очевидным для вызывающих объектов метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, пометьте метод или тип <xref:System.Security.SecurityCriticalAttribute> атрибутом.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Комментарии
