---
title: "CA1017: Помечайте сборки атрибутом ComVisibleAttribute | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1cf713e2c177a24938c44c4577da88d8943e4fef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: помечайте сборки атрибутом ComVisibleAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Сборка не имеет <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> атрибут, применяемый к нему.  
  
## <a name="rule-description"></a>Описание правила  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> Атрибута определяет порядок обращения клиентов COM к управляемого кода. Для правильной разработки сборки должны явным образом указывать видимость COM. Видимость COM можно задать для всей сборки и затем переопределить для отдельных типов и членов типов. Если атрибут отсутствует, содержимое сборки будет видимым клиентам COM.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте атрибут к сборке. Если вы не хотите сборки будет видимым клиентам COM., примените атрибут и присвойте ему значение `false`.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Если требуется, чтобы сборки были видимы, примените атрибут и присвойте ему значение `true`.  
  
## <a name="example"></a>Пример  
 В следующем примере показано сборку, которая имеет <xref:System.Runtime.InteropServices.ComVisibleAttribute> атрибут применяется, чтобы он не перестанут быть видимыми для COM-клиентам.  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## <a name="see-also"></a>См. также  
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)   
 [Oпределение типов .NET для взаимодействия](/dotnet/framework/interop/qualifying-net-types-for-interoperation)