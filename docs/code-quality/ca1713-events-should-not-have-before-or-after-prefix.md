---
title: CA1713. События не должны иметь префикс before или after
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8dba144740a2a39494323a456cddf90131e35c6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920331"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713. События не должны иметь префикс before или after

|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя события начинается с «Before» или «After».

## <a name="rule-description"></a>Описание правила
 Имена событий должны описывать действия, которое вызывает событие. Чтобы дать имена связанным событиям, возникающим в определенной последовательности, используйте настоящее или прошедшее время, чтобы обозначить положение события в последовательности действий. Например при именования пары событий, который вызывается при закрытии ресурс можно назвать его «Закрытие» и «Закрыто», а не «BeforeClose» и «AfterClose».

 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает обучения, необходимый для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите префикс из имени события и попробуйте изменить имя, используйте настоящее или прошедшее команды.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.