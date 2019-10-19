---
title: Предупреждения надежности | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 250eb10581858534ec6325a1bfb61d84bddac05a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603976"
---
# <a name="reliability-warnings"></a>предупреждения надежности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Предупреждения о надежности поддерживают надежность библиотек и приложений, например правильную память и использование потоков.

## <a name="in-this-section"></a>Содержание

|Правило|Описание|
|----------|-----------------|
|[CA2000: удалите объекты до того, как будет потеряна область действия](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Необходимо явно удалить объект до того, как все ссылки на него окажутся вне области действия, так как может произойти исключительное событие, которое воспрепятствует выполнению метода завершения объекта.|
|[CA2001: избегайте вызовов проблемных методов](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Член вызывает потенциально опасный или проблемный метод.|
|[CA2002: не блокировать объекты со слабой идентификацией](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|К объекту со слабой идентификацией может быть получен прямой доступ через границы домена приложения. Поток пытается получить блокировку объекта со слабой идентификацией, который может быть заблокирован вторым потоком в другом домене приложения, имеющим блокировку того же объекта.|
|[CA2003: не следует обрабатывать нити как потоки](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Управляемый поток обрабатывается как поток Win32.|
|[CA2004: удалите вызовы GC.KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|При преобразовании в использование SafeHandle удалите все вызовы GC. KeepAlive (объект). В этом случае классы не должны вызывать GC. KeepAlive, предполагая, что они не имеют метода завершения, но используют SafeHandle для окончательного завершения дескриптора ОС.|
|[CA2006: используйте SafeHandle для инкапсуляции машинных ресурсов](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Использование указателя IntPtr в управляемом коде может указывать на потенциальную проблему безопасности и надежности. Необходимо изучить все случаи использования указателя IntPtr, чтобы определить, не следует ли использовать вместо него класс SafeHandle или другую подобную технологию.|
