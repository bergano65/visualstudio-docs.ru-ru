---
title: 'CA1401: методы P-Invoke не должны быть видимыми | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9f13669959a5874c74753d304371b8ab7db14d4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547294"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: методы P/Invoke не должны быть видимыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод в открытом типе имеет <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибут (также реализуется с помощью `Declare` ключевого слова в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

## <a name="rule-description"></a>Описание правила
 Методы, помеченные <xref:System.Runtime.InteropServices.DllImportAttribute> атрибутом (или методами, определенными с помощью `Declare` ключевого слова in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ), используют службы вызова платформы для доступа к неуправляемому коду. Такие методы не следует делать видимыми. Сохранив эти методы как частные или внутренние, вы убедитесь, что библиотека не может быть использована для нарушения безопасности, разрешая вызывающим объектам доступ к неуправляемым API, которые им не удалось вызвать в противном случае.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените уровень доступа метода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере объявляется метод, нарушающий это правило.

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]
