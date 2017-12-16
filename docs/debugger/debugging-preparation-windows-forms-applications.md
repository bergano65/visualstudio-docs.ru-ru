---
title: "Подготовка к отладке: Приложения Windows Forms | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 873b7dd10a2e39aa795626bc7d387df7017740d8
ms.sourcegitcommit: 1e08318a8a684b21609af7a5e48b56abcc3239e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2017
---
# <a name="debugging-preparation-windows-forms-applications"></a>Подготовка к отладке: приложения Windows Forms
Шаблон проекта Windows Forms создает приложение Windows Forms. Отладка приложений такого типа в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не вызывает никаких затруднений. Дополнительные сведения см. в разделе [Создание проекта приложения Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 При создании проекта Windows Forms из шаблона проекта, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически создает требуемые параметры для отладки и выпуска. При необходимости эти параметры можно изменить. Эти параметры могут быть изменены в  **\<имя проекта > страницы свойств** диалоговое окно (**Мой проект** в Visual Basic).  
  
 Дополнительные сведения см. в разделе [рекомендуемые параметры свойств](../debugger/managed-debugging-recommended-property-settings.md).  
  
 В следующей таблице приведены дополнительные параметры, рекомендуемые к использованию.  
  
### <a name="configuration-properties-in-debug-tab"></a>"Свойства конфигурации" во вкладке "Отладка"  
  
|**Имя свойства**|**Параметр**|  
|-----------------------|-----------------|  
|**Действие при запуске**|-Значение **Открытие проекта** большую часть времени. Значение **запуск внешней программы** Если требуется запускать другой исполняемый файл при запуске отладки (обычно для отладки DLL).|  
  
 Можно выполнять отладку приложений Windows Forms из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или путем присоединения к уже запущенному приложению. Дополнительные сведения о присоединении см. в разделе [присоединение к процессу под управлением](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Выполнение отладки приложения Windows Forms на C#, F# или Visual Basic  
  
1.  Откройте проект в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Создайте точки останова, если требуется.  
  
     Поскольку приложения Windows Forms управляются событиями, точки останова появятся в коде обработчиков событий, или в методах, вызываемых ими. Типичные события, в которые стоит помещать точки останова:  
  
    1.  события, связанные с элементом управления, такие как Click, Enter, и т.д.;  
  
    2.  события, связанные с запуском приложений и завершением работы, такие как Load, Activated и т. д.;  
  
    3.  события, связанные с фокусом и проверками.  
  
     Подробнее см. в разделе [Создание обработчиков событий в Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).  
  
3.  На **отладки** меню, нажмите кнопку **запустить**.  
  
4.  Отладка с помощью способов, приведенных в [основы отладчик](../debugger/debugger-basics.md).  
  
## <a name="see-also"></a>См. также  
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)   
 [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Как: набор отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Параметры проекта для конфигураций отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Присоединение к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](/dotnet/framework/winforms/index)