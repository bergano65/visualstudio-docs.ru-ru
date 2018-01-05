---
title: "CA1411: Методы регистрации COM не должны быть видимыми | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 43b1f340b62726edc33b3e7e05d52634c2a2595b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411: методы регистрации для COM-клиента не должны быть видимыми
|||  
|-|-|  
|TypeName|ComRegistrationMethodsShouldNotBeVisible|  
|CheckId|CA1411|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Метод, который отмечен атрибутом <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> атрибута видим извне.  
  
## <a name="rule-description"></a>Описание правила  
 Когда сборка регистрируется с помощью модели объектов компонентов (COM), добавляются записи в реестре для каждого типа, видимый для модели COM в сборку. Методы, помеченные с <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> и <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> атрибуты называются во время процессов регистрации и отмены регистрации, соответственно, для выполнения пользовательского кода, характерное для регистрации или отмены регистрации этих типов. Этот код не должен вызываться за пределами этих процессов.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, измените уровень доступа для метода `private` или `internal` (`Friend` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано два метода, которые нарушают правила.  
  
 [!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1410: методы регистрации для COM-клиента должны быть соответствующими](../code-quality/ca1410-com-registration-methods-should-be-matched.md)  
  
## <a name="see-also"></a>См. также  
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>   
 [Регистрация сборок в COM](/dotnet/framework/interop/registering-assemblies-with-com)   
 [Regasm.exe (средство регистрации сборок)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)