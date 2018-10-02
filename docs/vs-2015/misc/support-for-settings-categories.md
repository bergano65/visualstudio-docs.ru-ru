---
title: Поддержка категорий параметров | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- settings, supporting with Visual Studio SDK
- Visual Studio SDK, supporting settings
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
manager: douge
ms.openlocfilehash: 474537895af5c51c7abd7439b58f8ef5994bdc11
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563085"
---
# <a name="support-for-settings-categories"></a>Поддержка категорий параметров
Категория параметров состоит из группы параметров, предназначенных для настройки интегрированной среды разработки (IDE). Например, параметры позволяют управлять макетом окон [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и содержимым меню. Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 В меню **Сервис** щелкните элемент **Импорт и экспорт параметров** , чтобы запустить **Мастер импорта и экспорта параметров**. Мастер предлагает три варианта: экспорт, импорт или сброс параметров. Например, при выборе экспорта открывается мастер **Выбор параметров для экспорта** .  
  
 Элемент управления деревом на панели навигации этой страницы перечисляет категории. Категория — это группа связанных параметров, которые отображаются в виде "точки настраиваемых параметров", то есть в виде флажка. Используйте эти флажки для выбора категорий, сохраняемых в файле VSETTINGS. Мастер позволяет задать имя для файла VSETTINGS и указать путь к нему.  
  
> [!NOTE]
>  Параметры сохраняются и восстанавливаются в составе категории — имена отдельных параметров в мастере не отображаются.  
  
 Платформа Managed Package Framework (MPF) поддерживает создание категорий параметров с минимальным объемом дополнительного кода.  
  
-   Для получения пакета VSPackage, используемого в качестве контейнера для категории, можно создать подкласс класса <xref:Microsoft.VisualStudio.Shell.Package>.  
  
-   Вы создаете саму категорию, сделав ее производной от класса <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
-   Для соединения этих двух компонентов используется <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="support-for-settings-categories"></a>Поддержка категорий параметров  
 Класс <xref:Microsoft.VisualStudio.Shell.Package> обеспечивает поддержку для создания категорий. Класс <xref:Microsoft.VisualStudio.Shell.DialogPage> реализует категорию. Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage> предлагает пользователю свои общие свойства в виде категории. Дополнительные сведения см. в разделе [Creating a Settings Category](../extensibility/creating-a-settings-category.md).  
  
 Класс <xref:Microsoft.VisualStudio.Shell.DialogPage> реализует <xref:Microsoft.VisualStudio.Shell.IProfileManager>, который обеспечивает сохраняемость как для страниц параметров, так и для параметров пользователя. Методы <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> и <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> сохраняют параметры в файле VSSETTINGS, который [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] предоставляет как <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> или <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>, соответственно. Метод <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A> выполняет сброс параметров в значения по умолчанию.  
  
 Класс <xref:Microsoft.VisualStudio.Shell.DialogPage> предоставляет реализацию метода <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A>, который считывает пары "имя-значение" из веб-канала XML, и использует отражение для обнаружения общих свойств в производном классе <xref:Microsoft.VisualStudio.Shell.DialogPage>. Свойствам, которые имеют имена, совпадающие с парами "имя-значение", присваиваются соответствующие значения.  
  
 Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> использует отражение для обнаружения общих свойств в производном классе <xref:Microsoft.VisualStudio.Shell.DialogPage> и записывает значения и имена свойств в веб-канала XML в виде пар "имя-значение".  
  
### <a name="settings-category-registry-path"></a>Путь реестра для категории параметров  
 Путь реестра для категории параметров определяется объединением <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, слова, UserSettings, категории параметров и имени точки настраиваемых параметров. Имена категории параметров и точки настраиваемых параметров объединяются и разделяются символом подчеркивания для формирования канонического нелокализованного имени, которое отображается в реестре. Например, если категория параметров называется "My Category", имя точки настраиваемых параметров имеет значение "My Settings", а ApplicationRegistryRoot — HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, то эта категория параметров имеет раздел реестра HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\UserSettings\My Category_My Settings.  
  
> [!NOTE]
>  Каноническое имя не отображается в пользовательском интерфейсе. Оно используется для сопоставления считываемого имени с категорией параметров, что во многом аналогично программному идентификатору (ProgID).  
  
### <a name="settings-category-attribute"></a>Атрибут категории параметров  
 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Определяет сопоставление категорий с точками настраиваемых параметров в **мастер импорта и экспорта параметров** путем связывания категории с пакетом VSPackage, который его предоставляет. Рассмотрим следующий фрагмент кода:  
  
 [!code-csharp[VSSDKSupportForSettingsCategories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforsettingscategories/cs/vssdksupportforsettingscategoriespackage.cs#1)]
 [!code-vb[VSSDKSupportForSettingsCategories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforsettingscategories/vb/vssdksupportforsettingscategoriespackage.vb#1)]  
  
 Идентификатор ресурса 106 сопоставляется с "My Category", 107 — с "My Settings", а 108 — с "Various Options". Этот код объявляет, что `MyPackage` предоставляет категорию "My Category_My Settings". Категория предоставляется классом `OptionsPageGeneral`, который должен реализовывать <xref:Microsoft.VisualStudio.Shell.IProfileManager>. Параметры в этой категории являются общедоступными свойствами класса `OptionsPageGeneral` .  
  
 Точка параметров в **мастере импорта и экспорта параметров**имеет имя "My Settings". При выборе точки параметров отображается описание **Various Options**. Имя и описание точки параметров берутся из локализованных строковых ресурсов.  
  
## <a name="see-also"></a>См. также  
 [Создание страницы параметров](../extensibility/creating-an-options-page.md)   
 [Примеры VSSDK](../misc/vssdk-samples.md)   
 [Состояние VSPackage](../misc/vspackage-state.md)   
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)