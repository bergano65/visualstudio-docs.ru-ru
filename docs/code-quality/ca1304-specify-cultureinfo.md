---
title: "CA1304: Укажите CultureInfo | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 932ac7e8f731974896991cea5ae504e452e9a036
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: укажите CultureInfo
|||  
|-|-|  
|TypeName|SpecifyCultureInfo|  
|CheckId|CA1304|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Метод или конструктор вызывает член, имеющий перегрузку, которая принимает <xref:System.Globalization.CultureInfo?displayProperty=fullName> не вызывает перегрузку, которая принимает параметр и метод или конструктор <xref:System.Globalization.CultureInfo> параметра. Данное правило пропускает вызовы следующих методов:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## <a name="rule-description"></a>Описание правила  
 Когда <xref:System.Globalization.CultureInfo> или <xref:System.IFormatProvider?displayProperty=fullName> не предоставляется, значение по умолчанию, поставляемое перегруженным членом может не иметь ожидаемого воздействия во всех языковых стандартах. Кроме того [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] элементов выберите язык и региональные параметры по умолчанию и исходя из предположения, которые могут не подходить для кода. Чтобы убедиться, что код работает должным образом для сценариев, необходимо предоставить сведения о культуре, согласно следующим правилам:  
  
-   Если значение будет отображаться для пользователя, используется текущий язык и региональные параметры. См. раздел <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Если значения будут храниться и использоваться программой, то есть, сохраняется в файл или базу данных, используйте инвариантного языка и региональных параметров. См. раздел <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Если вы не знаете назначение значения, потребитель данных или поставщик указать язык и региональные параметры.  
  
 Обратите внимание, что <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> используется только для извлечения локализованных ресурсов с помощью экземпляра <xref:System.Resources.ResourceManager?displayProperty=fullName> класса.  
  
 Даже если поведение по умолчанию перегруженного члена, соответствующий вашим потребностям, лучше явно вызвать перегрузку конкретного языка и региональных параметров, чтобы код самодокументируемыми и более простую обслуживаемую.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, используйте перегрузку, которая принимает <xref:System.Globalization.CultureInfo> или <xref:System.IFormatProvider> и указывать аргумент согласно правилам, перечисленные ранее.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила, когда известно, что поставщик языка и региональных параметров и формат по умолчанию является правильным выбором, а там, где простота модификации кода не является важным разработки приоритет.  
  
## <a name="example"></a>Пример  
 В следующем примере `BadMethod` вызывает два нарушения данного правила. `GoodMethod`исправляет первого нарушения путем передачи System.String.Compare инвариантного языка и региональных параметров и исправляет второй нарушение путем передачи текущего языка и региональных параметров для <xref:System.String.ToLower%2A> из-за `string3` отображается для пользователя.  
  
 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]  
  
## <a name="example"></a>Пример  
 В следующем примере показано влияние текущего языка и региональных параметров по умолчанию <xref:System.IFormatProvider> , выбран по <xref:System.DateTime> типа.  
  
 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]  
  
 В этом примере формируются следующие данные:  
  
 **6/4/1900 12:15:12 PM**  
**06/04/1900 12:15:12**   
## <a name="related-rules"></a>Связанные правила  
 [CA1305: укажите IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)  
  
## <a name="see-also"></a>См. также  
[С помощью класса CultureInfo](/dotnet/standard/globalization-localization/globalization#Cultures)  