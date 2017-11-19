---
title: "CA1016: Помечать сборки атрибутом AssemblyVersionAttribute | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 414a533e781be82cd0ffef1e9db234738ef07f16
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: помечать сборки атрибутом AssemblyVersionAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithAssemblyVersion|  
|CheckId|CA1016|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Сборка имеет номер версии.  
  
## <a name="rule-description"></a>Описание правила  
 Удостоверение сборки состоит из следующих сведений:  
  
-   Имя сборки  
  
-   Номер версии  
  
-   Язык и региональные параметры  
  
-   Открытый ключ (для сборок со строгими именами).  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] использует номер версии для уникального обозначения сборки и для привязки к типам в сборках со строгими именами. Номер версии используется наряду с политикой версий и издателя. По умолчанию приложения выполняются только с версией сборки, которая использовалась для их построения.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавить номер версии сборки с помощью <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> атрибута. См. следующий пример.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте предупреждение из этого правила для сборок, используемых сторонними разработчиками, или в рабочей среде.  
  
## <a name="example"></a>Пример  
 В следующем примере показано сборку, которая имеет <xref:System.Reflection.AssemblyVersionAttribute> применен атрибут.  
  
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## <a name="see-also"></a>См. также  
 [Управление версиями сборок](/dotnet/framework/app-domains/assembly-versioning)   
 [Практическое руководство. Создание политики издателя](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)