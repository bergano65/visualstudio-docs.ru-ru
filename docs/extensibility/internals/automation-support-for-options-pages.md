---
title: Поддержка автоматизации для страниц параметров | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03360bfc01110e7b4ef73956f0199aaaed9cee2c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848969"
---
# <a name="automation-support-for-options-pages"></a>Поддержка автоматизации для страниц параметров
Пакеты VSPackage могут предоставить диалоговые окна настраиваемых **параметров** меню **Сервис** (**Сервис параметры** ) в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] и сделать их доступными для модели автоматизации.

## <a name="tools-options-pages"></a>Сервис Параметры - страницы
 Для создания страницы **параметров средств** пакет VSPackage должен предоставить реализацию пользовательского элемента управления, возвращаемую в среду, с помощью реализации метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> в VSPackage. (Или для управляемого кода — метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>.)

 Это необязательно, но настоятельно рекомендуется, чтобы разрешить доступ к этой новой странице через модель автоматизации. Это можно сделать, выполнив следующие действия.

1. Расширьте объект <xref:EnvDTE._DTE.Properties%2A> с помощью реализации объекта, производного от IDispatch.

2. Возвращает реализацию метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> (или для управляемого кода метода <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A>) в объект, производный от IDispatch.

3. Когда потребитель автоматизации вызывает метод <xref:EnvDTE._DTE.Properties%2A> на странице свойств настраиваемого **параметра** , среда использует метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> для получения реализации автоматизации настраиваемой страницы **параметров средств** .

4. Затем объект автоматизации VSPackage используется для предоставления каждого <xref:EnvDTE.Property>, возвращаемого <xref:EnvDTE._DTE.Properties%2A>.

   Пример реализации настраиваемой страницы **параметров средств** см. в разделе [VSSDK Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>См. также:
- [Предоставление доступа к объектам проекта](../../extensibility/internals/exposing-project-objects.md)
