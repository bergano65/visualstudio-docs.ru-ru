---
title: "CA2124: помещайте уязвимые предложения finally во внешний блок try | Microsoft Docs"
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
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
helpviewer_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2124: помещайте уязвимые предложения finally во внешний блок try
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|WrapVulnerableFinallyClausesInOuterTry|  
|CheckId|CA2124|  
|Категория|Microsoft.Security|  
|Критическое изменение|Не критическое|  
  
## Причина  
 В версиях 1.0 и 1.1 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], открытый или защищенный метод содержит блок `try`\/ `catch`\/ `finally`.  Блок `finally` сбрасывает состояние безопасности не заключен в блок `finally`.  
  
## Описание правила  
 Это правило находит блоки `try`\/`finally` в коде, метящем версии 1.0 и 1.1 платформы [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], которые могут быть уязвимы для вредоносных фильтров исключений в стеке вызова.  Если в блоке try происходят важные операции, такие как олицетворение, и возникает исключения, то фильтр может быть выполнен до блока `finally`.  В случае с олицетворением фильтр будет выполнен от имени олицетворенного пользователя.  В настоящее время фильтры можно реализовать только в Visual Basic.  
  
> [!WARNING]
>  **Примечание** В версии 2.0 и более поздних версий [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], среда выполнения автоматически защищает блок `try`\/ `catch`\/ `finally` от вредоносных фильтров исключений, если происходит сброс непосредственно в методе, который содержит блок исключений.  
  
## Устранение нарушений  
 Поместите распакованный блок `try`\/`finally` во внешний блок try.  См. второй пример ниже.  При этом блок `finally` будет выполнен перед кодом фильтра.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример псевдокода  
  
### Описание  
 В следующем примере псевдокода показан шаблон, обнаруживаемый этим правилом.  
  
### Код  
  
```  
try {  
   // Do some work.  
   Impersonator imp = new Impersonator("John Doe");  
   imp.AddToCreditCardBalance(100);  
}  
finally {  
   // Reset security state.  
   imp.Revert();  
}  
```  
  
## Пример  
 В следующем примере псевдокода показан шаблон, который можно использовать для защиты кода и выполнения этого правила.  
  
```  
try {  
     try {  
        // Do some work.  
     }  
     finally {  
        // Reset security state.  
     }  
}  
catch()  
{  
    throw;  
}  
```