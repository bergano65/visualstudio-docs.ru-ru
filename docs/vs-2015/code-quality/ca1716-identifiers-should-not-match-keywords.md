---
title: 'CA1716: Идентификаторы не должны совпадать с ключевыми словами | Документация Майкрософт'
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
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c1a3affbecf7a39ee323fd64bc8a56d92e8a4d5e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591207"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: идентификаторы не должны совпадать с ключевыми словами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1716: идентификаторы не должны совпадать с ключевыми словами](https://docs.microsoft.com/visualstudio/code-quality/ca1716-identifiers-should-not-match-keywords).

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя пространства имен, тип или член виртуального члена или интерфейс совпадает с зарезервированным ключевым словом в языке программирования.

## <a name="rule-description"></a>Описание правила
 Идентификаторы пространств имен, типов и виртуальные и члены интерфейса не должны совпадать с ключевыми словами, которые определены в языках, поддерживаемых среда CLR. В зависимости от используемого языка и ключевого слова ошибки компилятора и неоднозначностей могут затруднять библиотеку для использования.

 Это правило проверяет ключевые слова на следующих языках:

-   Visual Basic

-   C#

-   C++/CLI

 Сравнение без учета регистра, используемый для [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ключевые слова и сравнение с учетом регистра используется для других языков.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Выберите имя, которое не отображается в списке ключевых слов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно подавить предупреждение из этого правила, если вы уверены, что идентификатор не будет запутывания пользователей API-интерфейса, и что библиотеку можно использовать в некоторых языках [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].



