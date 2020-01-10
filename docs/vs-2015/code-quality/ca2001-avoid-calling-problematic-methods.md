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
ms.openlocfilehash: 6a2ed905f8291bf503217239cc287c50b970572f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851724"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: избегайте вызовов проблемных методов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Категория|Microsoft. надежность|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
 Член вызывает потенциально опасный или проблемный метод.

## <a name="rule-description"></a>Описание правила
 Старайтесь не делать ненужные и потенциально опасные вызовы методов.

 Нарушение этого правила возникает, когда член вызывает один из следующих методов.

|Метод|Описание|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Вызов GC. Получение может существенно повлиять на производительность приложения и редко бывает необходимым. Дополнительные сведения см. в записи блога "Mariani's" для [tidbits производительности](https://blogs.msdn.com/ricom/archive/2004/11/29/271829.aspx) на сайте MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. Suspend и Thread. Resume устарели из-за непредсказуемого поведения.  Используйте другие классы в пространстве имен <xref:System.Threading>, такие как <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>и <xref:System.Threading.Semaphore>, для синхронизации потоков или защиты ресурсов.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Метод DangerousGetHandle создает угрозу безопасности, поскольку он может возвращать недопустимый маркер. Дополнительные сведения об безопасном использовании метода DangerousGetHandle см. в описании методов <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> и <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A>.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Эти методы могут загружать сборки из непредвиденных расположений. Например, дополнительные сведения о методах, которые загружают сборки, см. в блоге о Сузаннеах .NET CLR Notes в записях блога [LoadFile vs. LoadFrom](https://blogs.msdn.com/suzcook/archive/2003/09/19/loadfile-vs-loadfrom.aspx) и [выборе контекста привязки](https://blogs.msdn.com/suzcook/archive/2003/05/29/57143.aspx) на веб-сайте MSDN.|
|[CoSetProxyBlanket](https://msdn.microsoft.com/library/ms692692.aspx) (ole32)<br /><br /> [CoInitializeSecurity](https://msdn.microsoft.com/library/ms693736.aspx) (ole32)|К моменту, когда пользовательский код начинает выполняться в управляемом процессе, он слишком поздно для надежного вызова метода CoSetProxyBlanket. Среда CLR принимает действия инициализации, которые могут препятствовать выполнению P/Invoke пользователями.<br /><br /> Если необходимо вызвать метод CoSetProxyBlanket для управляемого приложения, рекомендуется запустить процесс с помощью исполняемого файла машинного кода (C++), вызвать CoSetProxyBlanket в машинном коде, а затем запустить приложение управляемого кода в процессе. (Не забудьте указать номер версии среды выполнения.)|

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите или замените вызов опасного или проблемного метода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Сообщения из этого правила следует подавлять только в том случае, если не существует альтернативы проблемному методу.

## <a name="see-also"></a>См. также раздел
 [Предупреждения надежности](../code-quality/reliability-warnings.md)
