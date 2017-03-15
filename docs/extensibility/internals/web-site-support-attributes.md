---
title: "Веб-узел поддержки атрибуты | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: dba1aeb8f8e3ad368f050ef425f76cc6c94f99e8
ms.lasthandoff: 02/22/2017

---
# <a name="web-site-support-attributes"></a>Атрибуты веб-сайта поддержки
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Проект веб-сайта можно расширить для обеспечения поддержки веб-языков программирования. Язык должен зарегистрироваться с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для отображения шаблонов проектов можно в **новый веб-сайт** диалоговое окно при выборе языка.  
  
 Пример IronPython Studio включает поддержку веб-сайта. Его можно найти с помощью [VSSDK примеры](../../misc/vssdk-samples.md). Он включает следующие классы атрибутов зарегистрировать IronPython в качестве фонового кода языка для новых веб-проектов.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Этот атрибут следует поместить в проекте языка. Он добавляет язык в список языков в веб-программирования **язык** список **новый веб-сайт** диалоговое окно. Например добавляет IronPython в список:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Этот атрибут также задает путь к папке шаблонов шаблоны. Дополнительные сведения о расположении «шаблоны» в разделе [шаблоны веб-сайт поддержки](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Этот атрибут следует поместить в проекте языка. Он позволяет проекта веб-сайта вложить один тип файла (связано) в файл другого типа (основной) в **обозревателе решений**.  
  
 Пример:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Указывает, что файл фонового кода IronPython связана с ASPX-файла. При создании новой веб-страницы .aspx в решении IronPython Web site, новый источник py-файл создается и отображается как дочерний узел ASPX-страницы.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Этот атрибут следует поместить на язык пакета проекта. Он выбирает поставщика Intellisense для языка.  
  
 Пример:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Указывает, что экземпляр PythonIntellisenseProvider, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, необходимо создать по требованию для предоставления служб языка.</xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>  
  
 Реализация IVsIntellisenseProject обрабатывает ссылки и вызывает компилятор языка, при запросе веб-страницы с кодом, но не кэшируется.  
  
## <a name="see-also"></a>См. также  
 [Поддержка веб-сайтов](../../extensibility/internals/web-site-support.md)
