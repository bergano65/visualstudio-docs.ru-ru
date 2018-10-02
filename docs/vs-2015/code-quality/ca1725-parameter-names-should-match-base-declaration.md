---
title: 'CA1725: Имена параметров должны соответствовать базовому объявлению | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 20a7e5f0239d572ec1867ffdac80f116cfd8360a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591964"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: имена параметров должны соответствовать базовому объявлению
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1725: имена параметров должны соответствовать базовому объявлению](https://docs.microsoft.com/visualstudio/code-quality/ca1725-parameter-names-should-match-base-declaration).

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя параметра в видимом извне методе переопределения не соответствует имени параметра в базовом объявлении метода или имя параметра в объявлении интерфейса метода.

## <a name="rule-description"></a>Описание правила
 Согласованное именование параметров в иерархии переопределений увеличивает удобство использования переопределений метода. Если имя параметра в производном методе отличается от имени в базовом объявлении, может возникнуть путаница в определении того, чем является метод: переопределением базового метода или новой перегрузкой.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, переименуйте параметр, чтобы соответствовать базовому объявлению. Исправление является критическим изменением для методов, видимых COM.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте предупреждение из этого правила, за исключением методов, видимых COM в библиотеках, которые были предоставлены ранее.



