---
title: "CA1401: методы P вызывает должен не быть видимым | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 707c78c6101c3cec554efe0f6957e4f08c059c3a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: методы P/Invoke не должны быть видимыми
|||  
|-|-|  
|TypeName|PInvokesShouldNotBeVisible|  
|CheckId|CA1401|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Открытый или защищенный метод в открытом типе имеет <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> атрибут (также реализован `Declare` ключевое слово в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="rule-description"></a>Описание правила  
 Методы, помеченные с <xref:System.Runtime.InteropServices.DllImportAttribute> атрибута (или методы, определенные с помощью `Declare` ключевое слово в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) использовать службы вызова платформы для доступа к неуправляемому коду. Такие методы не следует делать видимыми. Сохраняя эти методы private или internal, вы убедитесь, что библиотека не может использоваться для прорыва безопасности путем предоставления вызывающим объектам доступ к неуправляемым API, которые в противном случае они не вызвать.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените уровень доступа метода.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере объявляется метод, который нарушает это правило.  
  
 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]