---
title: предупреждения надежности
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74c1a5202b05b3ffe6f9b6c5b24804fb259287c4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942730"
---
# <a name="reliability-warnings"></a>предупреждения надежности
Предупреждения надежности поддерживают безотказность библиотек и приложений, таких как правильное использование памяти и потоков.

## <a name="in-this-section"></a>В этом разделе

|Правило|Описание:|
|----------|-----------------|
|[CA2000: Ликвидировать объекты перед потерей области](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Необходимо явно удалить объект до того, как все ссылки на него окажутся вне области действия, так как может произойти исключительное событие, которое воспрепятствует выполнению метода завершения объекта.|
|[CA2001: Избегайте вызовов проблемных методов](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Член вызывает потенциально опасный или проблемный метод.|
|[CA2002: Не блокировать объекты со слабой идентификацией](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|К объекту со слабой идентификацией может быть получен прямой доступ через границы домена приложения. Поток пытается получить блокировку объекта со слабой идентификацией, который может быть заблокирован вторым потоком в другом домене приложения, имеющим блокировку того же объекта.|
|[CA2003: Не следует обрабатывать нити как потоки](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Управляемый поток обрабатывается как поток Win32.|
|[CA2004: Удалите вызов GC. KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|При переходе к использованию SafeHandle удалите все вызовы метода GC. KeepAlive (объект). В этом случае классы не следует вызывать сборки Мусора. Для их обработки KeepAlive, при условии, что они используют не метод завершения, а класс SafeHandle для завершения работы операционной системы.|
|[CA2006: Используйте SafeHandle для инкапсуляции машинных ресурсов](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Использование указателя IntPtr в управляемом коде может указывать на потенциальную проблему безопасности и надежности. Необходимо изучить все случаи использования указателя IntPtr, чтобы определить, не следует ли использовать вместо него класс SafeHandle или другую подобную технологию.|