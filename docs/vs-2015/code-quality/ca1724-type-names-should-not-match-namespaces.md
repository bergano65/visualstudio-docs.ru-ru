---
title: 'CA1724: имена типов не должны совпадать с именами пространства имен | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa0b73b6608f0dfd5daa4b770b7d780e64704c99
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544434"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724. Имена типов не должны совпадать с именами пространства имен
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя типа соответствует [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] именам пространств имен в сравнении без учета регистра.

## <a name="rule-description"></a>Описание правила
 Имена типов не должны совпадать с именами пространств имен, определенными в библиотеке классов [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Нарушение этого правила приводит к уменьшению функциональности библиотеки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Выберите имя типа, которое не соответствует имени [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] пространства имен библиотеки классов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для новой разработки нет известных сценариев, при которых необходимо отключить предупреждение из этого правила. Прежде чем подавить предупреждение, тщательно продумайте, как пользователи библиотеки могут быть скрыты по совпадающему имени. Для доставки библиотек может потребоваться отключить предупреждение из этого правила.
