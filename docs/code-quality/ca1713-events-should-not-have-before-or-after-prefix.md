---
title: 'CA1713: События не должны содержать префикс before или after | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3daa93429a59e0b6c3f03db0fc62dd7850df3be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: имена событий не должны содержать префикс "before" или "after"
|||  
|-|-|  
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|  
|CheckId|CA1713|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Имя события начинается с «Before» или «After».  
  
## <a name="rule-description"></a>Описание правила  
 Имена событий должны описывать действие, которое вызывает событие. Чтобы дать имена связанным событиям, возникающим в определенной последовательности, используйте настоящее или прошедшее время, чтобы обозначить положение события в последовательности действий. Например при возникновении именования пара событий, который вызывается при закрытии ресурса ей может имя «Закрытие» и «Закрыто», а не «BeforeClose» и «AfterClose».  
  
 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных общеязыковая среда выполнения. Это уменьшает обучения, необходимое для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана с тем, кто имеет опыт в разработке управляемого кода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Удалите префикс из имени события и попробуйте изменить имя, используйте настоящее или прошедшее время команды.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.