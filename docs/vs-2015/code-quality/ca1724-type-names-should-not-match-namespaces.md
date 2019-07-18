---
title: CA1724. Имена типов не должны совпадать с пространствами имен | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7fe95e08d2265baf06c6da265996ffcd579f0d1f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143187"
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724. Имена типов не должны совпадать с именами пространства имен
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя типа соответствует [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] имена пространств имен при сравнении без учета регистра.

## <a name="rule-description"></a>Описание правила
 Имена типов не должны совпадать с именами пространств имен, определенными в библиотеке классов [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Нарушение этого правила приводит к уменьшению функциональности библиотеки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Выберите имя типа, которое не соответствует имени [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] имен библиотеки классов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для разработки новых приложений, не известные сценарии возникнуть, когда необходимо подавить предупреждение из этого правила. Прежде чем можно подавить предупреждение, внимательно рассмотрите, каким образом пользователи библиотеки могут быть в замешательстве по соответствующим именем. Для доставки библиотек, возможно подавить предупреждение из этого правила.
