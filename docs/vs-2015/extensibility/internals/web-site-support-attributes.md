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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144299"
---
# <a name="web-site-support-attributes"></a>Атрибуты поддержки веб-сайтов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Проект веб-сайта можно расширить, чтобы обеспечить поддержку языков веб-программирования. Язык должен быть зарегистрирован в, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] поэтому шаблоны проектов могут отображаться в диалоговом окне **новый веб-сайт** при выборе языка.  
  
 Образец IronPython Studio включает в себя поддержку веб-сайтов. Его можно найти с помощью [примеров VSSDK](../../misc/vssdk-samples.md). Он включает следующие классы атрибутов для регистрации IronPython в качестве языка CodeBehind для новых веб-проектов.  
  
## <a name="websiteprojectattribute"></a>вебситепрожектаттрибуте  
 Этот атрибут размещается в проекте языка. Он добавляет язык в список языков веб-программирования в списке **язык** диалогового окна **новый веб-сайт** . Например, следующий пример добавляет IronPython в список:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Этот атрибут также задает путь к шаблонам для указания на папку Templates. Дополнительные сведения о расположении папки Templates см. в разделе [шаблоны поддержки веб-сайтов](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>вебситепрожектрелатедфилесаттрибуте  
 Этот атрибут размещается в проекте языка. Он позволяет проекту веб-сайта вкладывать один тип файла (связанный) в другой тип файла (основной) в **Обозреватель решений**.  
  
 Пример:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Указывает, что файл фонового кода IronPython связан с файлом. aspx. При создании новой веб-страницы. aspx в решении веб-сайта IronPython создается новый исходный файл с расширением «копировать», который отображается как дочерний узел страницы. aspx.  
  
## <a name="provideintellisenseproviderattribute"></a>провидеинтеллисенсепровидераттрибуте  
 Этот атрибут размещается в пакете языкового проекта. Он выбирает поставщик IntelliSense для языка.  
  
 Пример:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Указывает, что экземпляр Писонинтеллисенсепровидер, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> , должен быть создан по запросу для предоставления языковых служб.  
  
 Реализация Ивсинтеллисенсепрожект обрабатывает ссылки и вызывает компилятор языка, когда веб-страница с кодом запрашивается, но не кэшируется.  
  
## <a name="see-also"></a>См. также:  
 [Поддержка веб-сайтов](../../extensibility/internals/web-site-support.md)
