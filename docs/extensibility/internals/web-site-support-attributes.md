---
title: "Веб-сайт поддержки атрибуты | Документы Microsoft"
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
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 66e9dcfd511a95ce1ea27af64a3a7f8302fe2827
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
---
# <a name="web-site-support-attributes"></a>Атрибуты веб-сайта поддержки
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Проект веб-сайта можно расширить для поддержки для веб-языки программирования. Язык должен зарегистрироваться с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , чтобы шаблоны проектов могут присутствовать в **новый веб-сайт** диалоговое окно при выборе языка.

Пример IronPython Studio включает поддержку веб-сайта. Образец содержит следующие классы атрибутов, регистрируемый IronPython как codebehind язык для нового веб-проектов.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Этот атрибут следует поместить в проекте языка. Он добавляет языка в список языков в веб-программирования **язык** списка в **новый веб-сайт** диалоговое окно. Например следующий код добавляет IronPython списка:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Этот атрибут также задает шаблоны путь к папке «Шаблоны». Дополнительные сведения о расположении папки с шаблонами см. в разделе [шаблоны веб-сайта поддержки](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Этот атрибут следует поместить в проекте языка. Позволяет проекта веб-сайта вложить один тип файла (связано) в файл другого типа (основной) в **обозревателе решений**.

 Например следующий код указывает, что файл фонового кода IronPython связана с ASPX-файл. При создании нового веб-страницы .aspx в решении IronPython Web site новый исходный файл .py создается и отображается как дочерний узел на ASPX-страницу.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Этот атрибут следует поместить в языкового пакета проекта. Он выбирает поставщика IntelliSense для языка.

 Например, следующий код указывает, что экземпляр PythonIntellisenseProvider, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, необходимо создать по требованию для предоставления служб языка.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Реализация IVsIntellisenseProject обрабатывает ссылки и вызывает компилятор языка, при запросе веб-страницы с кодом, но не кэшируется.

## <a name="see-also"></a>См. также
 [Поддержка веб-сайтов](../../extensibility/internals/web-site-support.md)