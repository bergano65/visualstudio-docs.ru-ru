---
title: "Параллельная установка версий Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "параллельные установки [Visual Studio]"
  - "справка [Visual Studio], установка"
  - "Экспресс-выпуск [Visual Studio]"
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
caps.handback.revision: 47
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Параллельная установка версий Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эту версию Visual Studio можно установить на компьютер, на котором уже установлена более ранняя версия. В случае сбоя установки можно с помощью [средства сбора данных журнала](http://go.microsoft.com/fwlink/?LinkId=262077) собрать информацию о сбоях, чтобы самостоятельно найти причины неполадок.  
  
> [!NOTE]
>  Версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] рекомендуется устанавливать в порядке их выпуска. Например, Visual Studio 2013 необходимо устанавливать до Visual Studio 2015.  
  
 Прежде чем устанавливать несколько версий среды на одном компьютере, следует учесть следующие условия:  
  
-   При использовании Visual Studio 2015 для открытия решения, которое было создано в [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], можно впоследствии снова открыть и изменить решение в более ранней версии, если в нем не реализованы никакие функции, относящиеся только к Visual Studio 2015.  
  
-   При попытке открыть решение, которое было создано в [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] или более ранней версии, с помощью Visual Studio 2015 может потребоваться изменить проекты и файлы, чтобы они стали совместимы с Visual Studio 2015. Для получения дополнительной информации см. [Перенос, миграция и обновление проектов Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md).  
  
-   В случае удаления версии [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с компьютера, на котором установлено более одной версии, сопоставления файлов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] будут удалены для всех версий. Изменить сопоставления файлов можно с помощью кнопки **Восстановить сопоставления файлов** на станице **Среда**, **Общее** диалогового окна [Параметры](../ide/reference/general-environment-options-dialog-box.md).  
  
-   Visual Studio не обновляет расширения автоматически, так как не все расширения совместимы. Необходимо переустановить расширения из [коллекции Visual Studio](http://go.microsoft.com/fwlink/?LinkId=178891) или с помощью средств издателя программного обеспечения.  
  
## Версии платформы .NET Framework и установка нескольких версий на один компьютер  
  
-   В проектах Visual Basic, Visual C\# и Visual F\# параметр **Целевая рабочая среда** в **конструкторе проектов** используется для определения того, какая версию платформы .NET Framework используется в проекте. Для проекта C\+\+ можно вручную изменить целевую платформу, изменив VCXPROJ\-файл. Для получения дополнительной информации см. [Совместимость версий](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md).  
  
     При создании проекта можно указать целевую версию .NET Framework проекта в списке **.NET Framework** в диалоговом окне **Создание проекта**.  
  
     Сведения, относящиеся к конкретному языку, см. в соответствующем разделе следующей таблицы.  
  
    |Язык|Раздел|  
    |----------|------------|  
    |[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]|[Страница «Приложение» в конструкторе проектов \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)|  
    |Visual C\#|[Страница "Приложение" в конструкторе проектов \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)|  
    |Visual F\#|[Настройка проектов](../Topic/Configuring%20Projects%20\(F%23\).md)|  
    |C\+\+|[Практическое руководство. Изменение требуемой версии .NET Framework и набора средств платформы](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md)|  
    |[!INCLUDE[jsprjscript](../extensibility/debugger/includes/jsprjscript_md.md)]|[Запуск приложения JScript в предыдущей версии среды CLR](http://msdn.microsoft.com/ru-ru/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## См. также  
 [Установка Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)   
 [Перенос, миграция и обновление проектов Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Совместимость версий](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md)   
 [Установка нескольких языковых версий Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [Построение изолированных приложений и параллельных сборок C\/C\+\+](/visual-cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies)   
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3)