---
title: 'Подготовка к отладке: Веб-приложений ASP.NET | Документация Майкрософт'
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
ms.openlocfilehash: e7a2640d39c90dc36a3960d230df46ac75bdbce6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092426"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Подготовка к отладке: Веб-приложения ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Веб-сайт шаблон создает приложение веб-форму. При создании веб-узла с помощью этого шаблона [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] задает отладочные настройки по умолчанию. В **свойства проекта** диалоговом окне можно указать, следует ли веб-страницу стартовой. При запуске отладки [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]веб-сайта с этими параметрами по умолчанию [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] запускает Internet Explorer и присоединит отладчик к [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] рабочий процесс (aspnet_wp.exe или w3wp.exe). Дополнительные сведения см. в статье [System Requirements](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Создание приложения Web Forms  
  
1. На **файл** меню, выберите **новый веб-сайт**.  
  
2. В **новый веб-сайт** выберите [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **веб-сайт**.  
  
3. Нажмите кнопку **ОК**.  
  
### <a name="to-debug-your-web-form"></a>Отладка форм Web Forms  
  
1. Разместите точки останова в функциях и обработчиках событий.  
  
     Для получения дополнительной информации см. [Breakpoints and Tracepoints](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. Когда будет достигнута точка останова, выполните шаг с заходом внутрь этой функции. Наблюдайте за выполнением кода, пока не изолируете проблему.  
  
     Дополнительные сведения см. в разделе [пошаговое выполнение](http://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) и [отладки веб-приложений](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Изменение настроек по умолчанию  
 При желании можно изменить стандартные параметры конфигурации для отладки и конфигурации для выпуска, созданные [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [Как настроить конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Изменение используемых по умолчанию параметров конфигурации отладки  
  
1. В **обозревателе решений**, щелкните правой кнопкой мыши веб-сайт и выберите **страницы свойств** открыть **страницы свойств** диалоговое окно.  
  
2. Нажмите кнопку **параметры запуска**.  
  
3. Задайте **действие при запуске** на веб-страницу, которая должна отображаться первой.  
  
4. В разделе **отладчики**, убедитесь, что **Отладка ASP.NET** выбран.  
  
     Дополнительные сведения см. в разделе [параметры страниц свойств для веб-проектов](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>См. также  
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Основы отладки](../debugger/debugger-basics.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)
