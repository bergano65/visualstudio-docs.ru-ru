---
title: 'CA1725: имена параметров должны соответствовать базовому объявлению | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f1fb30cd37ebffcee7619190cef83560813b25db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547372"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725. Имена параметров должны соответствовать базовому объявлению
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя параметра в переопределении внешнего видимого метода не соответствует имени параметра в базовом объявлении метода или имени параметра в объявлении интерфейса метода.

## <a name="rule-description"></a>Описание правила
 Согласованное именование параметров в иерархии переопределений увеличивает удобство использования переопределений метода. Если имя параметра в производном методе отличается от имени в базовом объявлении, может возникнуть путаница в определении того, чем является метод: переопределением базового метода или новой перегрузкой.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, переименуйте параметр в соответствии с базовым объявлением. Исправление является критическим изменением для видимых методов COM.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, за исключением методов, видимых для COM, в библиотеках, которые были отгружены ранее.
