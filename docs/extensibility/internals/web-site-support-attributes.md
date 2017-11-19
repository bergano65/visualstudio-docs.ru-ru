---
title: "Веб-сайт поддержки атрибуты | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 504046999814b4766fa9e5e8c006a02049e7007d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="web-site-support-attributes"></a>Атрибуты веб-сайта поддержки
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Проект веб-сайта можно расширить для поддержки для веб-языки программирования. Язык должен зарегистрироваться с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , чтобы шаблоны проектов могут присутствовать в **новый веб-сайт** диалоговое окно при выборе языка.  
  
 Пример IronPython Studio включает поддержку веб-сайта. Он содержит следующие классы атрибутов для регистрации IronPython как codebehind язык для нового веб-проектов.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Этот атрибут следует поместить в проекте языка. Он добавляет языка в список языков в веб-программирования **язык** списка в **новый веб-сайт** диалоговое окно. Например следующие добавляет IronPython списка:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Этот атрибут также задает шаблоны путь к папке «Шаблоны». Дополнительные сведения о расположении папки с шаблонами см. в разделе [шаблоны веб-сайта поддержки](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Этот атрибут следует поместить в проекте языка. Позволяет проекта веб-сайта вложить один тип файла (связано) в файл другого типа (основной) в **обозревателе решений**.  
  
 Пример:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Указывает, что файл фонового кода IronPython связана с ASPX-файл. При создании нового веб-страницы .aspx в решении IronPython Web site новый исходный файл .py создается и отображается как дочерний узел на ASPX-страницу.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Этот атрибут следует поместить в языкового пакета проекта. Он выбирает поставщика Intellisense для языка.  
  
 Пример:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Указывает, что экземпляр PythonIntellisenseProvider, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, необходимо создать по требованию для предоставления служб языка.  
  
 Реализация IVsIntellisenseProject обрабатывает ссылки и вызывает компилятор языка, при запросе веб-страницы с кодом, но не кэшируется.  
  
## <a name="see-also"></a>См. также  
 [Поддержка веб-сайтов](../../extensibility/internals/web-site-support.md)