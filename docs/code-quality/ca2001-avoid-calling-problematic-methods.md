---
title: CA2001. Избегайте вызова проблемных методов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95209067f3821b6446b64dc7990e189720d20cea
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233192"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001. Избегайте вызова проблемных методов

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Категория|Microsoft. надежность|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Член вызывает потенциально опасный или проблемный метод.

## <a name="rule-description"></a>Описание правила

Старайтесь не делать ненужные и потенциально опасные вызовы методов. Нарушение этого правила возникает, когда член вызывает один из следующих методов:

|Метод|Описание|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Вызов GC. Получение может существенно повлиять на производительность приложения и редко бывает необходимым. Дополнительные сведения см. в записи блога "Mariani's" для [tidbits производительности](http://go.microsoft.com/fwlink/?LinkId=169256) на сайте MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. Suspend и Thread. Resume устарели из-за непредсказуемого поведения.  Используйте <xref:System.Threading> другие классы в пространстве имен, такие как <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>и <xref:System.Threading.Semaphore>, для синхронизации потоков или защиты ресурсов.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Метод DangerousGetHandle создает угрозу безопасности, поскольку он может возвращать недопустимый маркер. Дополнительные сведения <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> о безопасном использовании метода DangerousGetHandle см. в <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> методах и.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Эти методы могут загружать сборки из непредвиденных расположений. Например, см. статью сузаннеs. NET CLR notess [в блоге о LoadFile и LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) и [Выбор контекста привязки](http://go.microsoft.com/fwlink/?LinkId=164451) для получения сведений о методах, которые загружают сборки.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) Ole32<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) Ole32|К моменту, когда пользовательский код начинает выполняться в управляемом процессе, он слишком поздно для надежного вызова метода CoSetProxyBlanket. Среда CLR принимает действия инициализации, которые могут препятствовать выполнению P/Invoke пользователями.<br /><br /> Если необходимо вызвать метод CoSetProxyBlanket для управляемого приложения, рекомендуется запустить процесс с помощью исполняемого файла машинного кода (C++), вызвать CoSetProxyBlanket в машинном коде, а затем запустить приложение управляемого кода в процессе. (Не забудьте указать номер версии среды выполнения.)|

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, удалите или замените вызов опасного или проблемного метода.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Сообщения из этого правила следует подавлять только в том случае, если не существует альтернативы проблемному методу.

## <a name="see-also"></a>См. также

- [Предупреждения надежности](../code-quality/reliability-warnings.md)