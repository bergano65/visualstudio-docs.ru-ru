---
title: 'CA1725: Имена параметров должны соответствовать базовому объявлению | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d269d1f7bf373c9a0faedfe0f70b5192771fc4e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: имена параметров должны соответствовать базовому объявлению
|||  
|-|-|  
|TypeName|ParameterNamesShouldMatchBaseDeclaration|  
|CheckId|CA1725|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Имя параметра в переопределении Внешне видимый метод соответствует имени параметра в базовом объявлении метода или имя параметра в объявлении метода интерфейса.  
  
## <a name="rule-description"></a>Описание правила  
 Согласованное именование параметров в иерархии переопределений увеличивает удобство использования переопределений метода. Если имя параметра в производном методе отличается от имени в базовом объявлении, может возникнуть путаница в определении того, чем является метод: переопределением базового метода или новой перегрузкой.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, переименуйте параметр, чтобы соответствовать базовому объявлению. Исправление является критическим изменением для методов, видимых COM.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не отключайте предупреждение из этого правила, за исключением методов, видимых COM в библиотеках, которые были предоставлены ранее.