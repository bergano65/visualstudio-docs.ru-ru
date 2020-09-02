---
title: 'Подготовка к отладке: Windows Forms приложения | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [J#], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b11855fbd19dc464f92b4339684ef8346556c21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691151"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Подготовка к отладке: Приложения Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Шаблон проекта Windows Forms создает приложение Windows Forms. Отладка приложений такого типа в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] не вызывает никаких затруднений. Для получения дополнительной информации см. раздел [Создание проекта приложения Windows](https://msdn.microsoft.com/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 При создании проекта Windows Forms из шаблона проекта, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] автоматически создает требуемые параметры для отладки и выпуска. При необходимости эти параметры можно изменить. Эти параметры можно изменить в диалоговом окне ** \<project name> страницы свойств** (**Мой проект** в Visual Basic).  
  
 Дополнительные сведения см. в статье [Рекомендуемые параметры свойств](../debugger/managed-debugging-recommended-property-settings.md).  
  
 В следующей таблице приведены дополнительные параметры, рекомендуемые к использованию.  
  
### <a name="configuration-properties-in-debug-tab"></a>"Свойства конфигурации" во вкладке "Отладка"  
  
|**Имя свойства**|**Параметр**|  
|-----------------------|-----------------|  
|**Действие при запуске**|— Установите **Запуск проекта** в большинстве случаев. Установите **Запуск внешней программы**, если требуется запускать другой исполняемый файл при запуске отладки (обычно для отладки DLL).|  
  
 Можно выполнять отладку приложений Windows Forms из [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] или путем присоединения к уже запущенному приложению. См. сведения о [присоединении к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Выполнение отладки приложения Windows Forms на C#, F# или Visual Basic  
  
1. Откройте проект в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2. Создайте точки останова, если требуется.  
  
    Поскольку приложения Windows Forms управляются событиями, точки останова появятся в коде обработчиков событий, или в методах, вызываемых ими. Типичные события, в которые стоит помещать точки останова:  
  
   1. события, связанные с элементом управления, такие как Click, Enter, и т.д.;  
  
   2. события, связанные с запуском приложений и завершением работы, такие как Load, Activated и т. д.;  
  
   3. события, связанные с фокусом и проверками.  
  
      Подробнее см. в разделе [Создание обработчиков событий в Windows Forms](https://msdn.microsoft.com/library/6514e530-c6b8-489c-a8d2-eda7b7072701).  
  
3. В меню **Отладка** выберите команду **Запуск**.  
  
4. Отладка с использованием методик, описанных в разделе [основы отладчика](../debugger/debugger-basics.md).  
  
## <a name="see-also"></a>См. также:  
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)   
 [Типы проектов C#, F # и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Как задать конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Параметры проекта для конфигураций отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Присоединение к выполняющимся процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](https://msdn.microsoft.com/library/627df1e9-b254-41af-bbac-9a4f02810c54)
