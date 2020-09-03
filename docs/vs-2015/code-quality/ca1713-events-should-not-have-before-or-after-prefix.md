---
title: 'CA1713: события не должны иметь префикс Before или After | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b05c39a9d8a4a004359baf63919eb427c25fa5d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543966"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713. События не должны иметь префикс before или after
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя события начинается с "Before" или "After".

## <a name="rule-description"></a>Описание правила
 Имена событий должны описывать действие, которое вызывает событие. Чтобы дать имена связанным событиям, возникающим в определенной последовательности, используйте настоящее или прошедшее время, чтобы обозначить положение события в последовательности действий. Например, при именовании пары событий, создаваемых при закрытии ресурса, можно назвать его "Closing" и "Closed" вместо "BeforeClose" и "Афтерклосе".

 Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает кривую обучения, необходимую для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана кем-то, кто имеет опыт разработки управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите префикс из имени события и попробуйте изменить имя, чтобы оно использовало текущий или прошедшее время выполнения команды.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.
