---
title: 'CA2001: Избегайте вызовов проблемных методов | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ddc96857cf0c3c54472eded5545ca0f328eba213
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902793"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: избегайте вызовов проблемных методов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Категория|Microsoft.Reliability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Член вызывает потенциально опасный или проблемный метод.

## <a name="rule-description"></a>Описание правила
 Избегайте создания ненужных и потенциально опасных вызовов методов.

 Нарушение этого правила возникает, когда член вызывает один из следующих методов.

|Метод|Описание|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Вызов метода GC. Сбор может существенно повлиять на производительность приложения и требуется редко. Дополнительные сведения см. в разделе [Rico Mariani's Performance Tidbits](http://go.microsoft.com/fwlink/?LinkId=169256) запись в блоге на сайте MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Метод Thread.Suspend и Thread.Resume устарели из-за их к непредсказуемому поведению.  Используйте вместо него другие классы <xref:System.Threading> пространства имен, такие как <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, и <xref:System.Threading.Semaphore> для синхронизации потоков или защиты ресурсов.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Метод DangerousGetHandle создает угрозу безопасности, так как он может возвращать дескриптор, который является недопустимым. См. в разделе <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> и <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> Дополнительные сведения о том, как использовать метод DangerousGetHandle безопасно.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Эти методы могут загружать сборки из непредвиденных местах. Например, см. в разделе Сюзанны Кук по .NET CLR заметки в блогах [LoadFile vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) и [Выбор контекста привязки](http://go.microsoft.com/fwlink/?LinkId=164451) MSDN на веб-сайте сведения о методах загрузки сборок.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [Метод CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|Когда начинается выполнение кода пользователя в управляемого процесса уже поздно для надежного вызова CoSetProxyBlanket. Среда CLR (CLR) выполняет действия по инициализации, которые могут помешать успешному выполнению пользователей P/Invoke.<br /><br /> Если нужно вызвать CoSetProxyBlanket управляемого приложения, рекомендуется запустить процесс с помощью исполняемого машинного кода (C++), вызвать CoSetProxyBlanket в машинном коде и затем запустите приложение управляемого кода в процессе. (Не забудьте указать номер версии среды выполнения).|

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите или замените вызов опасный или проблемный метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Сообщения из этого правила следует отключать только в том случае, когда нет альтернативы проблемный метод доступны.

## <a name="see-also"></a>См. также
 [Предупреждения надежности](../code-quality/reliability-warnings.md)



