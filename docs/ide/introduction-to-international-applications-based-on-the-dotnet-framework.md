---
title: Знакомство с международными приложениями на платформе .NET Framework | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- strings [Visual Studio], localizing
- Web applications [.NET Framework], globalization
- Windows Forms, globalization
- localization [Visual Studio], culture setting
- fallback resources
- culture, setting
- globalization [Visual Studio], culture setting
- resources [Visual Studio], localization
- localization [Visual Studio], .NET localization model
- Assembly Resource file template
- resources [Visual Studio], fallback system
- international applications [Visual Studio], about international applications
- globalization [Visual Studio], international applications
- ASP.NET, globalization
- resource files, fallback processes
- user interface, culture setting
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: f2bbf16622e0f4bf1ca1478521881c42c34af56d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>Знакомство с международными приложениями на платформе .NET Framework
В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предусмотрено два компонента для создания международных приложений: глобализация — процесс разработки приложений, которые можно применять в различных культурах, и локализация — процесс перевода ресурсов для определенного языка и региональных параметров. Общие сведения о разработке приложений для международной аудитории см. в разделе [Рекомендации по разработке международных приложений](http://msdn.microsoft.com/Library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c).  
  
 Модель локализации [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] состоит из главной сборки, которая содержит код приложения и резервные ресурсы — строки, изображения и другие объекты для языка, на котором изначально разрабатывается приложение. Каждое локализованное приложение будет иметь вспомогательные сборки или сборки, содержащие только локализованные ресурсы. Так как основная сборка всегда содержит исходные резервные ресурсы, если ресурс не найден в локализованной вспомогательной сборке, <xref:System.Resources.ResourceManager> попытается загрузить его в виде иерархии, в конце концов добравшись до ресурсов в основной сборке. Система резервного использования ресурсов рассмотрена более подробно в разделе [Иерархическая организация ресурсов для локализации](../ide/hierarchical-organization-of-resources-for-localization.md).  
  
 Один из ресурсов локализации, который рекомендуется использовать, — это глоссарий для всех локализованных продуктов Майкрософт. Этот файл CSV содержит более 12 000 английских терминов и переводы на 59 разных языков. Глоссарий можно скачать на веб-странице [терминологии Майкрософт для переводов](http://go.microsoft.com/fwlink/?LinkId=128146).  
  
 Система проектов для приложений Windows Forms может создавать файлы ресурсов как для резервной, так и для каждой необходимой дополнительной культуры пользовательского интерфейса. Файл резервных ресурсов встроен в основную сборку, а файлы регионально-зависимых ресурсов встраиваются во вспомогательные сборки, по одному для каждого языка пользовательского интерфейса. При сборке проекта файлы ресурсов компилируются из формата Visual Studio XML (RESX) в промежуточный двоичный формат (RESOURCES) и затем внедряются во вспомогательные сборки.  
  
 Система работы с проектами для форм Windows Forms и Web Forms позволяет создать файлы ресурсов с помощью шаблона файла ресурсов сборки, получить доступ к ресурсам и выполнить сборку проекта. Вспомогательные сборки будут создаваться вместе с главной сборкой.  
  
 При выполнении локализованного приложения его внешний вид определяется двумя значениями языка и региональных параметров. (*Язык и региональные параметры* — это набор информации о предпочтениях пользователя, относящихся к языку пользователя, среде и правилам культуры.) Параметр языка и региональных параметров пользовательского интерфейса определяет, какие ресурсы будут загружаться. Язык и региональные параметры пользовательского интерфейса задаются как `UICulture` в файлах Web.config и директивах страниц, а также как <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> в коде Visual Basic или C#. Параметр языка и региональных параметров определяет формат значений, таких как даты, числа, валюта и так далее. Язык и региональные параметры задаются как `Culture` в файлах Web.config и директивах страниц, а также как <xref:System.Globalization.CultureInfo.CurrentCulture%2A> в коде Visual Basic или C#.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Globalization>   
 <xref:System.Resources>   
 [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)   
 [Безопасность и локализованные вспомогательные сборки](../ide/security-and-localized-satellite-assemblies.md)