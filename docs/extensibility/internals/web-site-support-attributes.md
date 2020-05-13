---
title: Атрибуты поддержки веб-сайта Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef75f99480145475278357a552f3ac74c0289800
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703501"
---
# <a name="web-site-support-attributes"></a>Атрибуты поддержки веб-сайтов
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Проект веб-сайта может быть расширен для поддержки языков веб-программирования. Язык должен зарегистрироваться [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] таким образом, чтобы шаблоны проектов могли отображаться в поле диалога **нового веб-узла** при выборе языка.

Образец IronPython Studio включает в себя поддержку веб-сайта. Выборка содержит следующие классы атрибутов для регистрации IronPython в качестве языка код-за ими для новых веб-проектов.

## <a name="websiteprojectattribute"></a>Веб-сайтПроектАattributeец
 Этот атрибут размещается в языковом проекте. Он добавляет язык в список языков веб-программирования в списке **языков** в новом диалоговом поле **Web Site.** Например, следующий код добавляет IronPython в список:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Этот атрибут также устанавливает путь шаблонов, чтобы указать на папку шаблонов. Для получения дополнительной информации о местоположении [Web Site Support Templates](../../extensibility/internals/web-site-support-templates.md)папки шаблонов см.

## <a name="websiteprojectrelatedfilesattribute"></a>Веб-сайтProjectRelatedFilesAttribute
 Этот атрибут размещается в языковом проекте. Это позволяет проекту website гнездить один тип файла (связанный) под другой тип файла (первичный) в **Solution Explorer.**

 Например, в следующем коде указывается, что кодовый файл IronPython связан с файлом .aspx. При создании новой веб-страницы .aspx в решении веб-узла IronPython создается новый исходный файл .py, который отображается в виде детского узла страницы .aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Этот атрибут размещается в пакете языкового проекта. Он выбирает поставщика IntelliSense для языка.

 Например, в следующем коде указывается, что экземпляр PythonIntellisenseProvider, который <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>реализует, должен быть создан по требованию для предоставления языковых услуг.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Реализация IVsIntellisenseProject обрабатывает ссылки и вызывает компилятор языка, когда веб-страница с кодом запрашивается, но не кэшируется.

## <a name="see-also"></a>См. также
- [Поддержка веб-сайтов](../../extensibility/internals/web-site-support.md)
