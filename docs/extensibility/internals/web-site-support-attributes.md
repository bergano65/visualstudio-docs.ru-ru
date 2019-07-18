---
title: Атрибуты поддержки веб-сайта | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a508acaf174e5e4e4b4b615e5f38c600f0669ed
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323383"
---
# <a name="web-site-support-attributes"></a>Атрибуты поддержки веб-сайтов
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Проект веб-сайта можно расширить для обеспечения поддержки веб-языков программирования. Язык должен зарегистрироваться с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] так, чтобы отображались шаблоны проектов можно в **новый веб-сайт** диалоговое окно, если выбран язык.

Пример IronPython Studio включает поддержку веб-сайта. Образец содержит следующие классы атрибутов для регистрации в качестве фонового кода язык для нового веб-проектов IronPython.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Этот атрибут следует поместить в проекте языка. Он добавляет языка в список языков в веб-программирования **языка** в списке **новый веб-сайт** диалоговое окно. Например следующий код добавляет IronPython в список:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Этот атрибут также задает путь к папке шаблонов шаблоны. Дополнительные сведения о расположении папки шаблонов см. в разделе [шаблоны веб-сайта поддержки](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Этот атрибут следует поместить в проекте языка. Он позволяет проекту веб-сайта вкладывать один тип файла (связанный) под другой тип файла (основной) в **обозревателе решений**.

 Например следующий код указывает, что файл фонового кода IronPython связана с ASPX-файл. При создании нового веб-страницы .aspx в решении IronPython Web site новый исходный файл .py создается и отображается как дочерний узел страницы с расширением ASPX.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Этот атрибут следует поместить в пакет языка проекта. Он выбирает поставщика IntelliSense для языка.

 Например, следующий код указывает, что экземпляр PythonIntellisenseProvider, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, должен будет создан по требованию для предоставления служб языка.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Реализация IVsIntellisenseProject обрабатывает ссылки и вызывает компилятор языка, когда запрашивается веб-страницы с кодом, но не кэшируется.

## <a name="see-also"></a>См. также
- [Поддержка веб-сайтов](../../extensibility/internals/web-site-support.md)