---
title: "CA1305: укажите IFormatProvider | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyIFormatProvider"
  - "CA1305"
helpviewer_keywords: 
  - "CA1305"
  - "SpecifyIFormatProvider"
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1305: укажите IFormatProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyIFormatProvider|  
|CheckId|CA1305|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Метод или конструктор вызывает один или несколько членов, имеющих перегрузки, которые принимают параметр <xref:System.IFormatProvider?displayProperty=fullName>, вместо того чтобы вызвать перегрузку, принимающую параметр <xref:System.IFormatProvider>.  Данное правило не распространяется на вызовы методов [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], которые в документации указаны как пропускающие параметр <xref:System.IFormatProvider>, а также на следующие методы:  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## Описание правила  
 Если объект <xref:System.Globalization.CultureInfo?displayProperty=fullName> или <xref:System.IFormatProvider> не предоставляется, значение по умолчанию, предоставляемое перегруженным членом, может не иметь ожидаемого результата во всех языковых стандартах.  Кроме того, члены [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] выбирают язык и региональные параметры, исходя из предположения, что этот выбор может быть неверен для данного кода.  Чтобы обеспечить правильную работу кода в сценариях, необходимо предоставить сведения о языке и региональных параметрах согласно приведенным ниже рекомендациям:  
  
-   Если значение отображается для пользователей, используйте текущий язык и региональные параметры.  См. раздел <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.  
  
-   Если значение предназначено для хранения и использования программным обеспечением \(сохраняется в файле или базе данных\), следует использовать инвариантный язык и региональные параметры.  См. раздел <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  
  
-   Если назначение значения неизвестно, язык и региональные параметры должны указываться объектом\-получателем или поставщиком данных.  
  
 Обратите внимание, что значение <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> используется только для извлечения локализованных ресурсов с помощью экземпляра класса <xref:System.Resources.ResourceManager?displayProperty=fullName>.  
  
 Возможно, поведение по умолчанию перегруженного члена соответствует потребностям разработчика, однако всегда лучше явно вызвать перегрузку, предоставляющую сведения о языке и региональных параметрах, чтобы получить самодокументируемый и более простой в обслуживании код.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, используйте перегрузку, которая принимает параметр <xref:System.Globalization.CultureInfo> или <xref:System.IFormatProvider>, и укажите аргумент в соответствии с ранее приведенными рекомендациями.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении данного правила будет безопасным в том случае, если доподлинно известно, что поставщик языка и региональных параметров, используемый по умолчанию, является правильным выбором, или удобство поддержки не является важным при разработке кода.  
  
## Пример  
 В следующем примере `BadMethod` приводит к двум нарушениям данного правила.  `GoodMethod` устраняет первое нарушение посредством передачи инвариантного языка и региональных параметров в <xref:System.String.Compare%2A>, а также устраняет второе нарушение путем передачи текущего языка и региональных параметров в <xref:System.String.ToLower%2A>, поскольку `string3` отображается для пользователя.  
  
 [!code-cs[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## Пример  
 В следующем примере показан результат передачи текущего языка и региональных параметров поставщику <xref:System.IFormatProvider> по умолчанию, выбранному типом <xref:System.DateTime>.  
  
 [!code-cs[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 В результате выполнения примера получается следующий результат:  
  
  **04.06.1900 12:15:12**  
**06\/04\/1900 12:15:12**   
## Связанные правила  
 [CA1304: укажите CultureInfo](../Topic/CA1304:%20Specify%20CultureInfo.md)  
  
## См. также  
 [NIB: Using the CultureInfo Class](http://msdn.microsoft.com/ru-ru/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)