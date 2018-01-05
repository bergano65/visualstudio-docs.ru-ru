---
title: "CA1305: Укажите IFormatProvider | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8bb3d993cc79ebf683f0a2622628bfc87d7c065a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: укажите IFormatProvider
|||  
|-|-|  
|TypeName|SpecifyIFormatProvider|  
|CheckId|CA1305|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Метод или конструктор вызывает один или несколько членов, имеющих перегрузки, принимающие <xref:System.IFormatProvider?displayProperty=fullName> не вызывает перегрузку, которая принимает параметр и метод или конструктор <xref:System.IFormatProvider> параметра. Это правило не учитывает вызовы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] методами, описанными как пропускающие <xref:System.IFormatProvider> параметра, а также следующие методы:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## <a name="rule-description"></a>Описание правила  
 Когда <xref:System.Globalization.CultureInfo?displayProperty=fullName> или <xref:System.IFormatProvider> не предоставляется, значение по умолчанию, поставляемое перегруженным членом может не иметь ожидаемого воздействия во всех языковых стандартах. Кроме того [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] элементов выберите язык и региональные параметры по умолчанию и исходя из предположения, которые могут не подходить для кода. Чтобы убедиться в том, что код работает должным образом для сценариев, необходимо предоставить сведения о культуре, согласно следующим правилам:  
  
-   Если значение будет отображаться для пользователя, используется текущий язык и региональные параметры. См. раздел <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Если значение будет храниться и доступ к программным обеспечением (сохраняется в базе данных или файл), использующие инвариантный язык. См. раздел <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Если вы не знаете назначение значения, потребитель данных или поставщик указать язык и региональные параметры.  
  
 Обратите внимание, что <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> используется только для извлечения локализованных ресурсов с помощью экземпляра <xref:System.Resources.ResourceManager?displayProperty=fullName> класса.  
  
 Даже если поведение по умолчанию перегруженного члена, соответствующий вашим потребностям, лучше явно вызвать перегрузку конкретного языка и региональных параметров, чтобы код самодокументируемыми и более простую обслуживаемую.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, используйте перегрузку, которая принимает <xref:System.Globalization.CultureInfo> или <xref:System.IFormatProvider> и указывать аргумент согласно правилам, перечисленные ранее.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это безопасно подавить предупреждение из этого правила, когда известно, что поставщик языка и региональных параметров и формат по умолчанию является правильным выбором и удобства поддержки кода не является важным разработки приоритет.  
  
## <a name="example"></a>Пример  
 В следующем примере `BadMethod` вызывает два нарушения данного правила. `GoodMethod`исправляет первого нарушения путем передачи инвариантного языка и региональных параметров для <xref:System.String.Compare%2A>и исправляет второй нарушение путем передачи текущего языка и региональных параметров для <xref:System.String.ToLower%2A> из-за `string3` отображается для пользователя.  
  
 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## <a name="example"></a>Пример  
 В следующем примере показано влияние текущего языка и региональных параметров по умолчанию <xref:System.IFormatProvider> , выбран по <xref:System.DateTime> типа.  
  
 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 В этом примере формируются следующие данные:  
  
 **6/4/1900 12:15:12 PM**  
**06/04/1900 12:15:12**   
## <a name="related-rules"></a>Связанные правила  
 [CA1304: укажите CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)  
  
## <a name="see-also"></a>См. также  
[С помощью класса CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)  