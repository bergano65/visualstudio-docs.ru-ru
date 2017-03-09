---
title: "Сохранение состояния и IDE Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "параметры IDE, сохранение состояния"
  - "пользовательские параметры [Visual Studio SDK], сохранение"
  - "страницы параметров средств [Visual Studio SDK], сохранение параметров"
  - "IDE, сохранение состояния"
  - "сохранение, пользовательские параметры"
ms.assetid: fdd49bb1-ed3b-4428-b685-de65c3215c1c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Сохранение состояния и IDE Visual Studio
**Параметры импорта\-экспорта** команда на  **Сервис** меню интегрированной среды разработки \(ide\) импортирования и экспортирует настройки  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] среда.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API параметров  [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] разрешить VSPackage, чтобы определить один или несколько категорий параметров \(группы в составе фазовые переменные\), который необходимо сохранить, когда пользователь выбирает  **Параметры импорта\-экспорта** команды.  
  
 Идентификатор GUID, однозначно определяющий каждый параметры категорию и указывается в собственной записи реестра именованной a *Параметры пользовательской точки*.  
  
> [!NOTE]
>  Стандартные реализации  **СервисПараметры** страницы  **Панель элементов**и  `Microsoft.VisualStudio.Shell.DialogPage` автоматическое предоставление поддержки для сохраняемости.  API параметров может переопределить механизм неисправный.  Дополнительные сведения см. в разделах [Расширение панели элементов](../misc/extending-the-toolbox.md), [Страницы параметров](../misc/options-pages.md) и <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
## В этом подразделе  
 [Поддержка параметров пользователя](../extensibility/internals/support-for-user-settings.md)  
 Описывает параметры реестра \(пользовательской точки параметров\) и атрибуты, используемые для определения a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] реализация параметров, заданных VSPackage.  
  
 [Практическое руководство. Экспорт параметров с помощью сборок взаимодействия](../misc/how-to-export-settings-by-using-interop-assemblies.md)  
 Содержит подробное описание, как реализовать поддержку для сохранения сведений о конфигурации с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] механизм параметров для сборки взаимодействия на основе VSPackages.  
  
 [Практическое руководство. Использование сборок взаимодействия для импорта параметров](../misc/how-to-use-interop-assemblies-to-import-settings.md)  
 Содержит подробное описание, как реализовать поддержку получение сведений о конфигурации с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] механизм параметров для сборки взаимодействия на основе VSPackages.  
  
 [Экспорт параметров](../misc/exporting-settings.md)  
 Включает подробное описание, как реализовать поддержку для сохранения сведений о конфигурации с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] механизм параметров для управляемого пакета .NET Framework определяется VSPackages.  
  
 [Импорт параметров](/visual-cpp/misc/importing-settings)  
 Содержит подробное описание, как реализовать поддержку получение сведений о конфигурации с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] механизм параметров для управляемого пакета .NET Framework определяется VSPackages.  
  
## Связанные подразделы  
 [Working with Settings](http://msdn.microsoft.com/ru-ru/4c0a56ab-6091-4ebc-9dc7-52c40846bacb)  
 Описывает, как управлять разделах экспорта и импорта интегрированной среды разработки.  
  
 [Страницы параметров](../misc/options-pages.md)  
 Описывает поддержку, [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] автоматически предоставляет для управления существовать или создать новый  **Сервис Параметры** веб\-страницы.  
  
 [Расширение панели элементов](../misc/extending-the-toolbox.md)  
 Объясняется поддержка, [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] автоматически предоставляет для управления или расширение  **Панель элементов**.  
  
 [Расширение настройки пользователя и параметры](../extensibility/extending-user-settings-and-options.md)  
 Описывает, как к программе в VSPackage получать и сохранять параметры пользователя.