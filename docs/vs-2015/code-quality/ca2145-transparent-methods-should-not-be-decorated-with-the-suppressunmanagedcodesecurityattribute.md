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
ms.openlocfilehash: 6bffa680fa39014ffa96feec997b5eca63ee08ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610212"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: прозрачные методы не должны быть снабжены атрибутом SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|транспарентмесодсшаулднотусесуппрессунманажедкодесекурити|
|CheckId|CA2145|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный метод, метод, помеченный методом <xref:System.Security.SecuritySafeCriticalAttribute>, или тип, содержащий метод, помечены атрибутом <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.

## <a name="rule-description"></a>Описание правила
 Методы, снабженные атрибутом <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>, имеют неявную проверку LinkDemand, накладываемую на любой метод, который его вызывает. Для этой проверки LinkDemand требуется, чтобы вызывающий код был критическим с точки зрения безопасности. Пометка метода, использующего SuppressUnmanagedCodeSecurity с атрибутом <xref:System.Security.SecurityCriticalAttribute>, делает это требование более очевидным для вызывающих объектов метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, пометьте метод или тип атрибутом <xref:System.Security.SecurityCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>Комментарии
