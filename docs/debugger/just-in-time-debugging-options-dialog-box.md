---
title: Just-In-Time, отладка, диалоговое окно параметров | Документы Microsoft
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
ms.openlocfilehash: 7be7dacbe7b3b89b8bdc09515c23d7597e7e55e5
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Страница "JIT-отладка", папка "Отладка", диалоговое окно "Параметры"
Чтобы получить доступ к **непосредственно в момент** перейдите в **средства** меню и выберите пункт **параметры**. В **параметры** диалогового окна разверните **Отладка** , а затем выберите **непосредственно в момент**. Эта страница позволяет включить JIT-отладку для управляемого кода, машинного кода и скриптов. Дополнительные сведения см. в разделе [JIT-отладка](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 JIT-отладку можно разрешить для программ следующих типов:  
  
-   Управляемый  
  
-   машинный код;  
  
-   Сценарий  
  
 JIT-отладка — это технология отладки программы, запускаемой вне [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Программу, созданную в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], можно выполнять вне среды [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Если включена JIT-отладка, сбой программы вызовет появление диалогового окна с вопросом о том, необходимо ли выполнить отладку.  
  
## <a name="associated-warnings"></a>Связанные предупреждения  
 При посещении этой страницы **параметры** диалоговое окно, может появиться предупреждающее сообщение следующим образом:  
  
 **Другой отладчик зарегистрировался как только время отладчика. Для восстановления включите непосредственно времени отладку или запустите средство восстановления Visual Studio.**  
  
 Это сообщение возникает, если в качестве JIT-отладчика установлен другой отладчик, возможно, отладчик [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] более старой версии.  
  
 Также возможно отображение следующего сообщения:  
  
 **В время обнаружены отладки ошибки регистрации. Для восстановления включите непосредственно времени отладку или запустите средство восстановления Visual Studio.**  
  
 Если вы видите, любое из этих предупреждений, просто времени отладки с [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] требуются права администратора до устранения проблем. Если попытаться разрешить проблему, не имея прав администратора, возникает следующее сообщение об ошибке:  
  
 **Отказано в доступе. Отладка администратора включить только времени или восстановите установку Visual Studio.**  
  
## <a name="see-also"></a>См. также  
 [Отладка, диалоговое окно параметров](../debugger/debugging-options-dialog-box.md)   
 [Практическое руководство. Установка параметров отладчика](../debugger/how-to-specify-debugger-settings.md)