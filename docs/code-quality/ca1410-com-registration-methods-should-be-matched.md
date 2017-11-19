---
title: "CA1410: Методы регистрации COM должны быть соответствующими | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 65c6191aff1433d050c1f7b50097c88d1d3cf2a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: методы регистрации для COM-клиента должны быть соответствующими
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldBeMatched|  
|CheckId|CA1410|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Тип объявляет метод, который отмечен атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> атрибута, но не объявляет метод, который отмечен атрибутом <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> атрибут, или наоборот.  
  
## <a name="rule-description"></a>Описание правила  
 Для объектов модели компонентов (COM) клиентам создавать [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] типа, этот тип должен быть зарегистрирован. Если он доступен, метод, который отмечен атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> атрибут вызывается в процессе регистрации для выполнения кода, определяемый пользователем. Соответствующий метод, который отмечен атрибутом <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> атрибут называется во время отмены регистрации для отката операций методом регистрации.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте соответствующий регистрации или отмены регистрации метод.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип, нарушающий правило. Исправление нарушения в примере комментариями.  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/CSharp/ca1410-com-registration-methods-should-be-matched_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../code-quality/codesnippet/VisualBasic/ca1410-com-registration-methods-should-be-matched_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1411: методы регистрации для COM-клиента не должны быть видимыми](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Регистрация сборок в COM](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (средство регистрации сборок)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)