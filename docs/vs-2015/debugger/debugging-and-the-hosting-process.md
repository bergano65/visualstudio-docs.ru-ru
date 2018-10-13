---
title: Отладка и ведущий процесс | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d3643e8a6c7bcb97d032771b4f98cbd926d9fd5a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249503"
---
# <a name="debugging-and-the-hosting-process"></a>Отладка и процесс размещения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В процессе размещения Visual Studio предусмотрены средства улучшения рабочих характеристик отладчика и новые возможности отладки, например, отладка с частичным доверием и вычисление выражения во время разработки. При необходимости процесс размещения можно отключить. Для получения дополнительной информации см. [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md). В следующих разделах описаны некоторые различия между отладкой с процессом размещения и отладкой без него.  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>Отладка с частичным доверием и модель безопасности Click-Once  
 Отладка с частичным доверием требует наличия процесса размещения. Если отключить процесс размещения, отладка кода с частичным доверием не будет работать даже в случае, если на странице **Безопасность** окна **Свойства проекта**включена защита в случае частичного доверия. Дополнительные сведения см. в разделах [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md) и [How to: Debug a Partial Trust Application](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## <a name="design-time-expression-evaluation"></a>Вычисление выражений в процессе разработки  
 Для вычисления выражений во время разработки всегда используется процесс размещения. Отключение процесса размещения в окне **Свойства проекта** отключает вычисление выражений во время разработки для проектов библиотек классов. Для других типов проектов вычисление выражений во время разработки не отключается. При этом Visual Studio запускает реальный исполняемый файл и использует его для вычислений во время разработки в отсутствие процесса размещения. Из-за этого результаты могут быть разными.  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>Различия для AppDomain.CurrentDomain.FriendlyName  
 `AppDomain.CurrentDomain.FriendlyName` возвращает различные результаты в зависимости от того, включен процесс размещения или нет. Если процесс размещения включен, вызов `AppDomain.CurrentDomain.FriendlyName` возвращает *имя_приложения*`.vhost.exe`. Если процесс размещения выключен, будет возвращено *имя_приложения*`.exe`.  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Различия для Assembly.GetCallingAssembly().FullName  
 `Assembly.GetCallingAssembly().FullName` возвращает различные результаты в зависимости от того, включен процесс размещения или нет. Если процесс размещения включен, вызов `Assembly.GetCallingAssembly().FullName` возвращает `mscorlib`. При вызове `Assembly.GetCallingAssembly().FullName` с отключенным процессом размещения будет возвращено имя приложения.  
  
## <a name="see-also"></a>См. также  
 [Ведущий процесс (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Практическое: отладка приложения с частичным доверием](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Практическое руководство. Отключение главного процесса](../ide/how-to-disable-the-hosting-process.md)



