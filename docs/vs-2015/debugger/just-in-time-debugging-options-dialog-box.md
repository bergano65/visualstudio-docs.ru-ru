---
title: Just-In-Time, отладка, диалоговое окно параметров | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 06fdd9d12003053ea6d992aa1d7d0fe9ed7144d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788138"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Страница "JIT-отладка", папка "Отладка", диалоговое окно "Параметры"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы получить доступ к **Just-In-Time** перейдите к странице **средства** меню и выберите пункт **параметры**. В **параметры** диалогового окна разверните узел **Отладка** узел и выберите **Just-In-Time**. Эта страница позволяет включить JIT-отладку для управляемого кода, машинного кода и скриптов. Дополнительные сведения см. в разделе [JIT-отладка](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 JIT-отладку можно разрешить для программ следующих типов:  
  
- Управляемый  
  
- машинный код;  
  
- Сценарий  
  
  JIT-отладка — это технология отладки программы, запускаемой вне [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Программу, созданную в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], можно выполнять вне среды [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Если включена JIT-отладка, сбой программы вызовет появление диалогового окна с вопросом о том, необходимо ли выполнить отладку.  
  
## <a name="associated-warnings"></a>Связанные предупреждения  
 При посещении этой страницы из **параметры** диалоговое окно может появиться предупреждающее сообщение следующим образом:  
  
 **Другой отладчик зарегистрировал себя как Just-In-Time отладчика. Для восстановления включите Just-In-Time отладку или запустите средство восстановления Visual Studio.**  
  
 Это сообщение возникает, если в качестве JIT-отладчика установлен другой отладчик, возможно, отладчик [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] более старой версии.  
  
 Также возможно отображение следующего сообщения:  
  
 **Just-In-Time обнаружены отладки ошибки регистрации. Для восстановления включите Just-In-Time отладку или запустите средство восстановления Visual Studio.**  
  
 Если вы видите одну из этих предупреждений, Just-In-Time отладки с помощью [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] требуются права администратора, пока не устранили проблему. Если попытаться разрешить проблему, не имея прав администратора, возникает следующее сообщение об ошибке:  
  
 **Доступ запрещен. Отладка администратора enable Just-In-Time, или восстановить установку Visual Studio.**  
  
## <a name="see-also"></a>См. также  
 [Отладка, диалоговое окно "Параметры"](../debugger/debugging-options-dialog-box.md)   
 [Практическое руководство. Установка параметров отладчика](../debugger/how-to-specify-debugger-settings.md)



