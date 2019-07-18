---
title: Атрибуты поддержки веб-сайта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75401eb0d5acd5d363d05aec57909eef5b9855e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68144299"
---
# <a name="web-site-support-attributes"></a>Атрибуты поддержки веб-сайтов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Проект веб-сайта можно расширить для обеспечения поддержки веб-языков программирования. Язык должен зарегистрироваться с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] так, чтобы отображались шаблоны проектов можно в **новый веб-сайт** диалоговое окно, если выбран язык.  
  
 Пример IronPython Studio включает поддержку веб-сайта. Его можно найти с помощью [примеры VSSDK](../../misc/vssdk-samples.md). Он включает в себя следующих классов атрибутов, регистрируемый в качестве фонового кода язык для нового веб-проектов IronPython.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Этот атрибут следует поместить в проекте языка. Он добавляет языка в список языков в веб-программирования **языка** в списке **новый веб-сайт** диалоговое окно. Например ниже добавляет IronPython в список:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Этот атрибут также задает путь к папке шаблонов шаблоны. Дополнительные сведения о расположении папки шаблонов см. в разделе [шаблоны веб-сайта поддержки](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Этот атрибут следует поместить в проекте языка. Он позволяет проекту веб-сайта вкладывать один тип файла (связанный) под другой тип файла (основной) в **обозревателе решений**.  
  
 Например:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Указывает, что файл фонового кода IronPython связана с ASPX-файл. При создании нового веб-страницы .aspx в решении IronPython Web site новый исходный файл .py создается и отображается как дочерний узел страницы с расширением ASPX.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Этот атрибут следует поместить в пакет языка проекта. Он выбирает поставщика Intellisense для языка.  
  
 Например:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Указывает, что экземпляр PythonIntellisenseProvider, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, должен будет создан по требованию для предоставления служб языка.  
  
 Реализация IVsIntellisenseProject обрабатывает ссылки и вызывает компилятор языка, когда запрашивается веб-страницы с кодом, но не кэшируется.  
  
## <a name="see-also"></a>См. также  
 [Поддержка веб-сайтов](../../extensibility/internals/web-site-support.md)
