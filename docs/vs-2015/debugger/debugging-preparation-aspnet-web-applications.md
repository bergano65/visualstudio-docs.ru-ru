---
title: 'Подготовка к отладке: веб-приложения ASP.NET | Документация Майкрософт'
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
- debugging ASP.NET Web applications
- debugging [Visual Studio], Web applications
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a80587062442688551d07128a2cec49a712adf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691462"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Подготовка к отладке: веб-приложения ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Шаблон веб-узла создает приложение веб-формы. При создании веб-узла с помощью этого шаблона [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] задает отладочные настройки по умолчанию. В диалоговом окне **Свойства проекта** можно указать, должна ли веб-страница быть начальной страницей. При запуске отладки [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] веб-сайта с этими параметрами по умолчанию [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] запускает Internet Explorer и подключает отладчик к [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] рабочему процессу (aspnet_wp.exe или w3wp.exe). Дополнительные сведения см. в статье [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Создание приложения Web Forms  
  
1. В меню **файл** выберите пункт **создать веб-сайт**.  
  
2. В диалоговом окне **новый веб-сайт** выберите [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **веб-сайт**.  
  
3. Нажмите кнопку **ОК**.  
  
### <a name="to-debug-your-web-form"></a>Отладка форм Web Forms  
  
1. Разместите точки останова в функциях и обработчиках событий.  
  
     Для получения дополнительной информации см. [Breakpoints and Tracepoints](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. Когда будет достигнута точка останова, выполните шаг с заходом внутрь этой функции. Наблюдайте за выполнением кода, пока не изолируете проблему.  
  
     Дополнительные сведения см. в разделе [пошаговое выполнение](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) и [Отладка веб-приложений и скриптов](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Изменение настроек по умолчанию  
 При желании можно изменить стандартные параметры конфигурации для отладки и конфигурации для выпуска, созданные [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [Практическое руководство. настроить конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Изменение используемых по умолчанию параметров конфигурации отладки  
  
1. В **Обозреватель решений**щелкните правой кнопкой мыши веб-сайт и выберите **страницы свойств** , чтобы открыть диалоговое окно **страницы свойств** .  
  
2. Щелкните **Параметры запуска**.  
  
3. Задайте **действие запуска** для веб-страницы, которая должна отображаться первой.  
  
4. В разделе **Отладчики**убедитесь, что выбрана **Отладка ASP.NET** .  
  
     Дополнительные сведения см. в разделе [параметры страниц свойств для веб-проектов](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>См. также:  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Основы отладчика](../debugger/debugger-basics.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)
