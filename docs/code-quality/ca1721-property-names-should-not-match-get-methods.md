---
title: "CA1721: Имена свойств не должны совпадать с методы get | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 91a280093d269797daa019b727bf2020462a0808
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: имена свойств не должны совпадать с именами методов get
|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Имя открытого или защищенного члена начинается с «Get» и в противном случае соответствует имени открытого или защищенного свойства. Например тип, который содержит метод с именем «GetColor» и свойство с именем «Color» нарушает это правило.  
  
## <a name="rule-description"></a>Описание правила  
 Методы get и свойства должны иметь имена, явно различающие их функции.  
  
 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных общеязыковая среда выполнения. Это уменьшает время, которое требуется изучать новую библиотеку программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана с тем, кто имеет опыт в разработке управляемого кода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Измените имя, чтобы он не соответствует имени метода, который начинается с «Get».  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
> [!NOTE]
>  Это предупреждение можно исключить, если причиной, реализовав интерфейс IExtenderProvider метода Get.  
  
## <a name="example"></a>Пример  
 В следующем примере содержится метод и свойство, которое нарушает это правило.  
  
 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1024: используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)