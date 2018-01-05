---
title: "CA2001: Избегайте вызовов проблемных методов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: da5da213d400f846f634a98dbdbe919cedf03bcd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: избегайте вызовов проблемных методов
|||  
|-|-|  
|TypeName|AvoidCallingProblematicMethods|  
|CheckId|CA2001|  
|Категория|Microsoft.Reliability|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Член вызывает потенциально опасный или проблемный метод.  
  
## <a name="rule-description"></a>Описание правила  
 Избегайте создания ненужных и потенциально опасных вызовов.  
  
 Нарушение этого правила возникает, когда член вызывает один из следующих методов.  
  
|Метод|Описание:|  
|------------|-----------------|  
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Вызов метода GC. Сбор может существенно повлиять на производительность приложения и требуется редко. Дополнительные сведения см. в разделе [Рико Мариани советы по повышению эффективности](http://go.microsoft.com/fwlink/?LinkId=169256) запись в блоге MSDN.|  
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Метод Thread.Suspend и Thread.Resume устарели из-за их к непредсказуемому поведению.  Использовать другие классы в <xref:System.Threading> пространства имен, такие как <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, <xref:System.Threading.Mutex>, и <xref:System.Threading.Semaphore> для синхронизации потоков или защиты ресурсов.|  
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Метод DangerousGetHandle создает угрозу безопасности, так как она может возвращать дескриптор, который не является допустимым. В разделе <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> и <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> Дополнительные сведения о том, как использовать метод DangerousGetHandle безопасно.|  
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Эти методы могут загружать сборки из непредвиденных местах. Пример в статье блога .NET CLR заметки Suzanne Cook [LoadFile vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) и [выбрав контекст привязки](http://go.microsoft.com/fwlink/?LinkId=164451) на веб-сайте MSDN сведения о методах, загружающие сборки.|  
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [Метод CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|К моменту начала выполнения в процессе управляемого кода пользователя уже слишком поздно для надежного вызова CoSetProxyBlanket. Общеязыковая среда выполнения (CLR) принимает инициализации действия, которые могут препятствовать успешному выполнению пользователей P/Invoke.<br /><br /> Если необходимо вызвать CoSetProxyBlanket управляемого приложения, рекомендуется запустить процесс с помощью исполняемого файла машинного кода (C++), вызвать CoSetProxyBlanket в машинном коде и затем запустите приложение управляемого кода в процессе. (Не забудьте указать номер версии среды выполнения).|  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите или замените вызов опасный или проблемный метод.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Сообщения из этого правила следует отключать только в том случае, когда нет альтернативы проблемный метод доступны.  
  
## <a name="see-also"></a>См. также  
 [Предупреждения надежности](../code-quality/reliability-warnings.md)