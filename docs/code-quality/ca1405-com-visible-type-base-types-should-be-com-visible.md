---
title: "CA1405: Базовые типы типу видимых COM должны быть видимыми для COM | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 91634d5d46d63165874deded9c5ac67e7d4afa07
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: базовые типы, относящиеся к типу видимых COM-клиенту, должны быть видимыми для COM
|||  
|-|-|  
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|DependsOnFix|  
  
## <a name="cause"></a>Причина  
 Видимый тип объектов модели компонентов (COM) является производным от типа, который не является видимым для COM.  
  
## <a name="rule-description"></a>Описание правила  
 Когда видимым для модели COM тип добавляет участников в новой версии, необходимо придерживаться строгим правилам, чтобы избежать нарушения COM-клиенты, которые привязаны к текущей версии. Тип, невидимый для COM, следование не должен следовать правилам управления версиями COM при добавлении новых членов. Однако если видимыми для COM тип является производным от типа невидимой COM и предоставляет интерфейс класса <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ClassInterfaceType> (по умолчанию), все открытые члены базового типа (если только они специально помечены как COM невидимым, который излишне) предоставляются COM. Если базовый тип добавляет новые члены в последующих версиях, могут нарушать работу всех клиентов COM, связанных с интерфейсом класса производного типа. Видимые COM-типы должны наследовать только от видимых COM типах снижения риска нарушения COM-клиентам.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, сделайте базовые типы видимыми для COM или производный тип COM невидимой.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий правило.  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Введение в интерфейс класса](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)