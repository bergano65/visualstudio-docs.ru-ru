---
title: Just-In-Time, отладка, диалоговое окно параметров | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6736e0646193754dbd932e5501a6473ee18c7e6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936333"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Страница "JIT-отладка", папка "Отладка", диалоговое окно "Параметры"
Чтобы получить доступ к **Just-In-Time** перейдите к странице **средства** меню и выберите пункт **параметры**. В **параметры** диалогового окна разверните узел **Отладка** узел и выберите **Just-In-Time**. Эта страница позволяет включить JIT-отладку для управляемого кода, машинного кода и скриптов. Дополнительные сведения см. в разделе [JIT-отладка](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 JIT-отладку можно разрешить для программ следующих типов:  
  
- Управляемый  
  
- машинный код;  
  
- Сценарий  
  
  JIT-отладка — это технология отладки программы, запускаемой вне [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Программу, созданную в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], можно выполнять вне среды [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Если включена JIT-отладка, сбой программы вызовет появление диалогового окна с вопросом о том, необходимо ли выполнить отладку.  
  
## <a name="associated-warnings"></a>Связанные предупреждения  
 При посещении этой страницы из **параметры** диалоговое окно может появиться предупреждающее сообщение следующим образом:  
  
 **Другой отладчик зарегистрировал себя как Just-In-Time отладчика. Для восстановления включите Just-In-Time отладку или запустите средство восстановления Visual Studio.**  
  
 Это сообщение возникает, если в качестве JIT-отладчика установлен другой отладчик, возможно, отладчик [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] более старой версии.  
  
 Также возможно отображение следующего сообщения:  
  
 **Just-In-Time обнаружены отладки ошибки регистрации. Для восстановления включите Just-In-Time отладку или запустите средство восстановления Visual Studio.**  
  
 Если вы видите одну из этих предупреждений, Just-In-Time отладки с помощью [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] требуются права администратора, пока не устранили проблему. Если попытаться разрешить проблему, не имея прав администратора, возникает следующее сообщение об ошибке:  
  
 **Доступ запрещен. Отладка администратора enable Just-In-Time, или восстановить установку Visual Studio.**  
  
## <a name="see-also"></a>См. также  
 [Отладка, диалоговое окно "Параметры"](../debugger/debugging-options-dialog-box.md)   
 [Практическое руководство. Установка параметров отладчика](../debugger/how-to-specify-debugger-settings.md)