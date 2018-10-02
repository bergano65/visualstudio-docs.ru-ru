---
title: 'CA1713: События не должны иметь префикс before или after | Документация Майкрософт'
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
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 46ed0ad62d145b7c60c9f20e1a3770016098a236
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591228"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: имена событий не должны содержать префикс "before" или "after"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1713: события не должны иметь префикс before или after](https://docs.microsoft.com/visualstudio/code-quality/ca1713-events-should-not-have-before-or-after-prefix).

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



