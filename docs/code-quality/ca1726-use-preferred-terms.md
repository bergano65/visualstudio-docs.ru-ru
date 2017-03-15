---
title: "CA1726: используйте предпочтительные термины | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsePreferredTerms"
  - "CA1726"
helpviewer_keywords: 
  - "UsePreferredTerms"
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# CA1726: используйте предпочтительные термины
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое — для сборок<br /><br /> Не критическое — если вызывается для параметров типов|  
  
## Причина  
 Имя видимого снаружи идентификатора включает термин, для которого существует другой предпочтительный термин.  Также это предупреждение возникает, если имя содержит термин Flag или Flags.  
  
## Описание правила  
 Это правило разделяет идентификатор на лексемы.  Каждая отдельная лексема и каждая последовательность двух лексем сравнивается с терминами, встроенными в правило, и с разделом устаревших терминов всех пользовательских словарей.  В следующей таблице показаны термины, встроенные в правило, и предпочтительные термины, которые следует использовать вместо первых.  
  
|Устаревший термин|Предпочтительный термин|  
|-----------------------|-----------------------------|  
|Arent|AreNot|  
|Отменено|Canceled|  
|Cant|Cannot|  
|ComPlus|EnterpriseServices|  
|Couldnt|CouldNot|  
|Didnt|DidNot|  
|Doesnt|DoesNot|  
|Dont|DoNot|  
|Flag или Flags|Замена отсутствует.  Не используется.|  
|Hadnt|HadNot|  
|Hasn’t|HasNot|  
|Havent|HaveNot|  
|Indices|Индексы|  
|Isnt|IsNot|  
|LogIn|LogOn|  
|LogOut|LogOff|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|SignOff|SignOut|  
|Wasnt|WasNot|  
|Werent|WereNot|  
|Wont|WillNot|  
|Wouldnt|WouldNot|  
|Writeable|Writable|  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, замените термин на аналогичный предпочтительный термин.  
  
## Отключение предупреждений  
 Предупреждения следует отключать только в том случае, если имя идентификатора выбрано намеренно вместо предпочтительного термина.  
  
## Связанные правила  
 [Предупреждения именования](../code-quality/naming-warnings.md)