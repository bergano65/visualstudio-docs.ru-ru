---
title: Страница "JIT-отладка", папка "Отладка", диалоговое окно "Параметры" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b3bd6c6ee32145a94dbc4b751834ecc003f2bdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201106"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Страница "JIT-отладка", папка "Отладка", диалоговое окно "Параметры"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы получить доступ к странице **JIT**, перейдите к меню **Сервис** и щелкните пункт **Параметры**. В диалоговом окне **Параметры** разверните узел **Отладка** и выберите **JIT**. Эта страница позволяет включить JIT-отладку для управляемого кода, машинного кода и скриптов. Дополнительные сведения см. в разделе [JIT-отладка](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 JIT-отладку можно разрешить для программ следующих типов:  
  
- Управляемый  
  
- машинный код;  
  
- Сценарий  
  
  JIT-отладка — это технология отладки программы, запускаемой вне [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Программу, созданную в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], можно выполнять вне среды [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Если включена JIT-отладка, сбой программы вызовет появление диалогового окна с вопросом о том, необходимо ли выполнить отладку.  
  
## <a name="associated-warnings"></a>Связанные предупреждения  
 При посещении этой страницы из диалогового окна **Параметры** можно увидеть предупреждающее сообщение, например следующего содержания:  
  
 **В качестве JIT-отладчика был зарегистрирован другой отладчик. Для восстановления включите JIT-отладку или запустите средство восстановления Visual Studio.**  
  
 Это сообщение возникает, если в качестве JIT-отладчика установлен другой отладчик, возможно, отладчик [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] более старой версии.  
  
 Также возможно отображение следующего сообщения:  
  
 **Обнаружены ошибки регистрации JIT-отладки. Для восстановления включите JIT-отладку или запустите средство восстановления Visual Studio.**  
  
 Если отобразилось любое из этих предупреждений, для JIT-отладки с [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] необходимы права администратора до тех пор, пока проблема не будет устранена. Если попытаться разрешить проблему, не имея прав администратора, возникает следующее сообщение об ошибке:  
  
 **Отказано в доступе. Администратор должен включить JIT-отладку или восстановить установку Visual Studio.**  
  
## <a name="see-also"></a>См. также:  
 [Отладка, диалоговое окно "Параметры"](../debugger/debugging-options-dialog-box.md)   
 [Практическое руководство. Установка параметров отладчика](../debugger/how-to-specify-debugger-settings.md)
