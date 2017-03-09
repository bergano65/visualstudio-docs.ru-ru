---
title: "Поддержка категорий параметров | Microsoft Docs"
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
  - "параметры, поддержка с помощью пакета SDK для Visual Studio"
  - "пакет SDK для Visual Studio, поддержка параметров"
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# Поддержка категорий параметров
Категория параметров состоит из группы параметров, предназначенных для настройки интегрированной среды разработки \(IDE\). Например, параметры позволяют управлять макетом окон [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и содержимым меню. Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 В меню **Сервис** щелкните элемент **Импорт и экспорт параметров**, чтобы запустить **Мастер импорта и экспорта параметров**. Мастер предлагает три варианта: экспорт, импорт или сброс параметров. Например, при выборе экспорта открывается мастер **Выбор параметров для экспорта**.  
  
 Элемент управления деревом на панели навигации этой страницы перечисляет категории. Категория — это группа связанных параметров, которые отображаются в виде "точки настраиваемых параметров", то есть в виде флажка. Используйте эти флажки для выбора категорий, сохраняемых в файле VSETTINGS. Мастер позволяет задать имя для файла VSETTINGS и указать путь к нему.  
  
> [!NOTE]
>  Параметры сохраняются и восстанавливаются в составе категории — имена отдельных параметров в мастере не отображаются.  
  
 Платформа Managed Package Framework \(MPF\) поддерживает создание категорий параметров с минимальным объемом дополнительного кода.  
  
-   Для получения пакета VSPackage, используемого в качестве контейнера для категории, можно создать подкласс класса <xref:Microsoft.VisualStudio.Shell.Package>.  
  
-   Вы создаете саму категорию, сделав ее производной от класса <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
-   Для соединения этих двух компонентов используется <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Поддержка категорий параметров  
 Класс <xref:Microsoft.VisualStudio.Shell.Package> обеспечивает поддержку для создания категорий. Класс <xref:Microsoft.VisualStudio.Shell.DialogPage> реализует категорию. Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage> предлагает пользователю свои общие свойства в виде категории. Для получения дополнительной информации см. [Создание категория параметров](../extensibility/creating-a-settings-category.md).  
  
 Класс <xref:Microsoft.VisualStudio.Shell.DialogPage> реализует <xref:Microsoft.VisualStudio.Shell.IProfileManager>, который обеспечивает сохраняемость как для страниц параметров, так и для параметров пользователя. Методы <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> и <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> сохраняют параметры в файле VSSETTINGS, который [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предоставляет как <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>, соответственно. Метод <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A> выполняет сброс параметров в значения по умолчанию.  
  
 Класс <xref:Microsoft.VisualStudio.Shell.DialogPage> предоставляет реализацию метода <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A>, который считывает пары "имя\-значение" из веб\-канала XML, и использует отражение для обнаружения общих свойств в производном классе <xref:Microsoft.VisualStudio.Shell.DialogPage>. Свойствам, которые имеют имена, совпадающие с парами "имя\-значение", присваиваются соответствующие значения.  
  
 Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> использует отражение для обнаружения общих свойств в производном классе <xref:Microsoft.VisualStudio.Shell.DialogPage> и записывает значения и имена свойств в веб\-канала XML в виде пар "имя\-значение".  
  
### Путь реестра для категории параметров  
 Путь реестра для категории параметров определяется объединением <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, слова, UserSettings, категории параметров и имени точки настраиваемых параметров. Имена категории параметров и точки настраиваемых параметров объединяются и разделяются символом подчеркивания для формирования канонического нелокализованного имени, которое отображается в реестре. Например, если категория параметров называется "My Category", имя точки настраиваемых параметров имеет значение "My Settings", а ApplicationRegistryRoot — HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp, то эта категория параметров имеет раздел реестра HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\UserSettings\\My Category\_My Settings.  
  
> [!NOTE]
>  Каноническое имя не отображается в пользовательском интерфейсе. Оно используется для сопоставления считываемого имени с категорией параметров, что во многом аналогично программному идентификатору \(ProgID\).  
  
### Атрибут категории параметров  
 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> определяет сопоставление категорий с точками настраиваемых параметров в **мастере импорта и экспорта параметров** путем связывания категории с пакетом VSPackage, который ее предоставляет. Рассмотрим следующий фрагмент кода:  
  
 [!code-vb[VSSDKSupportForSettingsCategories#1](../misc/codesnippet/VisualBasic/support-for-settings-categories_1.vb)]
 [!code-cs[VSSDKSupportForSettingsCategories#1](../misc/codesnippet/CSharp/support-for-settings-categories_1.cs)]  
  
 Идентификатор ресурса 106 сопоставляется с "My Category", 107 — с "My Settings", а 108 — с "Various Options". Этот код объявляет, что `MyPackage` предоставляет категорию "My Category\_My Settings". Категория предоставляется классом `OptionsPageGeneral`, который должен реализовывать <xref:Microsoft.VisualStudio.Shell.IProfileManager>. Параметры в этой категории являются общедоступными свойствами класса `OptionsPageGeneral`.  
  
 Точка параметров в **мастере импорта и экспорта параметров** имеет имя "My Settings". При выборе точки параметров отображается описание **Various Options**. Имя и описание точки параметров берутся из локализованных строковых ресурсов.  
  
## См. также  
 [Создание страницы параметров](../extensibility/creating-an-options-page.md)   
 [Примеры VSSDK](../misc/vssdk-samples.md)   
 [Состояние VSPackage](/visual-cpp/misc/vspackage-state)   
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3)