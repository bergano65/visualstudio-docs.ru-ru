---
title: Поддержка автоматизации для страниц опций (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe45238948d5b4cdebbf9f002f6b242515e7622e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709935"
---
# <a name="automation-support-for-options-pages"></a>Поддержка автоматизации страниц Опционов
VSPackages может предоставить пользовательские **варианты** диалоговых коробок [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для меню **инструментов** (страницы**опций инструментов)** и сделать их доступными для модели автоматизации.

## <a name="tools-options-pages"></a>Сервис Параметры - страницы
 Для создания **страницы «Параметры инструментов»** VSPackage должен обеспечить реализацию управления пользователем, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> возвращенную в среду через реализацию метода VSPackage. (Или, для управляемого <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> кода, метод.)

 Это необязательно, но настоятельно рекомендуется, чтобы обеспечить доступ к этой новой странице через модель автоматизации. Вы можете сделать это следующими шагами:

1. Расширяйте <xref:EnvDTE._DTE.Properties%2A> объект за счет реализации объекта, полученного из IDispatch.

2. Верните реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (или для <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> управляемого кода) объекту, полученному из IDispatch.

3. Когда <xref:EnvDTE._DTE.Properties%2A> потребитель автоматизации вызывает метод на странице свойств пользовательского **варианта,** среда использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> метод для получения реализации автоматизации страницы пользовательских **опций инструментов.**

4. Объект автоматизации VSPackage затем используется для <xref:EnvDTE.Property> обеспечения каждого возвращенного. <xref:EnvDTE._DTE.Properties%2A>

   Для примера реализации пользовательской **страницы Параметры инструментов,** см [VSSDK Образцы](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>См. также
- [Экспозиция объектов проекта](../../extensibility/internals/exposing-project-objects.md)
