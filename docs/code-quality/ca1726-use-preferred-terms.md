---
title: "CA1726: Используйте предпочтительные термины | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords: UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ae02d0eb136d45bc2b8af7dde5f897765493050
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: используйте предпочтительные термины
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое — для сборок<br /><br /> Не критическое — при возникновении в параметрах типов|  
  
## <a name="cause"></a>Причина  
 Имя видимого снаружи идентификатора включает термин, для которого существует другой предпочтительный термин. Кроме того имя содержит термин Flag или Flags.  
  
## <a name="rule-description"></a>Описание правила  
 Это правило анализирует идентификатор на лексемы. Каждая отдельная лексема и каждое непрерывное сочетание двух токенов сравнивается с термины, которые встроены в правило и в разделе не рекомендуемые к использованию всех пользовательских словарей. В следующей таблице показаны термины, которые встроены в правило и их предпочтительный альтернатив.  
  
|Устаревший термин|Предпочтительный термин|  
|-------------------|--------------------|  
|не|Не|  
|Отменено|Отменено|  
|Не удается|Не удается|  
|ComPlus|EnterpriseServices|  
|Couldnt|Невозможно|  
|Didnt|DidNot|  
|Doesnt|Не|  
|Не следует|Не будут|  
|Flag или Flags|Нет не заменяющего термина. Не используется.|  
|еще не|HadNot|  
|Не|HasNot|  
|еще не|HaveNot|  
|Индексы|Indexes|  
|не|IsNot|  
|Имя входа|Вход в систему|  
|Выход|Выход из системы|  
|Shouldnt|ShouldNot|  
|Входа|Вход|  
|Подпись|Выход|  
|Wasnt|WasNot|  
|не были|WereNot|  
|Не|WillNot|  
|Wouldnt|WouldNot|  
|Для записи|Для записи|  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, замените термин аналогичный предпочтительный термин.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила только в том случае, если имя идентификатора намеренно и посвящен исходный термин вместо предпочтительный термин.  
  
## <a name="related-rules"></a>Связанные правила  
 [Предупреждения именования](../code-quality/naming-warnings.md)