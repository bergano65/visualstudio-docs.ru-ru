---
title: "CA2144: прозрачный код не должен загружать сборки из массивов байтов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2144"
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA2144: прозрачный код не должен загружать сборки из массивов байтов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|  
|CheckId|CA2144|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Прозрачный метод загружает сборку из массива байтов с помощью одного из следующих методов:  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
## Описание правила  
 Проверка безопасности для прозрачного кода не так тщательна, как проверка безопасности для критического кода, поскольку прозрачный код не может выполнять действия, требующие особых мер безопасности.  Сборки, загруженные из массива байтов, могут остаться незамеченными в прозрачном коде, и этот массив байтов может содержать критичный или, что более важно, критичный в плане безопасности код, который подлежит аудиту.  Поэтому прозрачный код не должен загружать сборки из массивов байтов.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, отметьте метод, загружающий сборку, атрибутом <xref:System.Security.SecurityCriticalAttribute> или <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 Это правило срабатывает на следующий код, так как прозрачный метод загружает сборку из массива байтов:  
  
 [!code-cs[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]