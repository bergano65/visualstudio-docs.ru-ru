---
title: 'CA2001: Избегайте вызова проблемных методов | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 318b7b8adddd674a9b8ecb93441d69a76ab574dd
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586773"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001. Избегайте вызова проблемных методов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Категория|Microsoft. надежность|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Член вызывает потенциально опасный или проблемный метод.

## <a name="rule-description"></a>Описание правила
 Старайтесь не делать ненужные и потенциально опасные вызовы методов.

 Нарушение этого правила возникает, когда член вызывает один из следующих методов.

|Метод|Описание|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Вызов GC. Получение может существенно повлиять на производительность приложения и редко бывает необходимым. Дополнительные сведения см. в записи блога "Mariani's" для [tidbits производительности](https://docs.microsoft.com/archive/blogs/ricom/when-to-call-gc-collect) на сайте MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. Suspend и Thread. Resume устарели из-за непредсказуемого поведения.  Используйте другие классы <xref:System.Threading> в пространстве имен, например <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, и <xref:System.Threading.Semaphore> для синхронизации потоков или защиты ресурсов.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Метод DangerousGetHandle создает угрозу безопасности, поскольку он может возвращать недопустимый маркер. Дополнительные сведения <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> о безопасном использовании метода DangerousGetHandle см. в <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> методах и.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Эти методы могут загружать сборки из непредвиденных расположений. Например, дополнительные сведения о методах, которые загружают сборки, см. в блоге о Сузаннеах .NET CLR Notes в записях блога [LoadFile vs. LoadFrom](https://docs.microsoft.com/archive/blogs/suzcook/loadfile-vs-loadfrom) и [выборе контекста привязки](https://docs.microsoft.com/archive/blogs/suzcook/choosing-a-binding-context) на веб-сайте MSDN.|
|[CoSetProxyBlanket](https://msdn.microsoft.com/library/ms692692.aspx) (ole32)<br /><br /> [CoInitializeSecurity](https://msdn.microsoft.com/library/ms693736.aspx) (ole32)|К моменту, когда пользовательский код начинает выполняться в управляемом процессе, он слишком поздно для надежного вызова метода CoSetProxyBlanket. Среда CLR принимает действия инициализации, которые могут препятствовать выполнению P/Invoke пользователями.<br /><br /> Если вам нужно вызвать метод CoSetProxyBlanket для управляемого приложения, рекомендуется запустить этот процесс с помощью исполняемого файла машинного кода (C++), вызвать метод CoSetProxyBlanket в машинном коде, а затем запустить приложение управляемого кода в процессе. (Не забудьте указать номер версии среды выполнения.)|

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите или замените вызов опасного или проблемного метода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Сообщения из этого правила следует подавлять только в том случае, если не существует альтернативы проблемному методу.

## <a name="see-also"></a>См. также
 [Предупреждения о надежности](../code-quality/reliability-warnings.md)
