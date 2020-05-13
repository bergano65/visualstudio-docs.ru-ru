---
title: Глиф управления (Источник управления VSPackage) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9db1b4542eae293e39cda674fac3eb984aa77d3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708322"
---
# <a name="glyph-control-source-control-vspackage"></a>Контроль glyph (управление источником VSPackage)
Частью глубокой интеграции, доступной для управления исходным управлением VSPackages, является возможность отображения собственных глифов для обозначения состояния элементов под контролем источника.

## <a name="levels-of-glyph-control"></a>Уровни контроля глифов
 Глайф состояния — это значок, указывающий текущее состояние элемента при отображении, например в **Solution Explorer** или в **представлении класса.** Управление источником VSPackage может осуществлять два уровня управления глифом. Он может ограничить выбор глифов предопределенным набором глифов, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предоставляемых IDE, или определить пользовательский набор глифов для отображения.

### <a name="default-set-of-glyphs"></a>По умолчанию набор глифов
 Для определения состояния глифов, связанных с элементом в **Solution Explorer,** проект запрашивает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>состояние глифа из элемента управления исходом с помощью . Управление источником VSPackage может принять решение сохранить выбор глифов ограничивается предопределенными глифами, предоставляемыми IDE. В этом случае VSPackage передает назад массив значений, представляющих glyph enumerations, которые определяются в *vsshell.idl.* Для получения дополнительной информации см. <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Это предопределенный набор глифов, установленный IDE, например, замок для проверенного глифа, и контрольный знак для проверенного глифа.

### <a name="custom-set-of-glyphs"></a>Пользовательский набор глифов
 Управление источником VSPackage может использовать свои собственные глифы для уникального взгляда и ощущения при установке. Когда новый элемент управления исходным ресурсом VSPackage активен, он должен быть в состоянии начать использовать свои собственные глифы, даже если предыдущий элемент управления исходным элементом VSPackage по-прежнему загружен, но неактивен. В этом режиме управление исходным элементом VSPackage по-прежнему может [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использовать существующие значки для поддержания вида, согласующегося с, если он выбирает.

 Услуга <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> поддерживает интерфейс, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>который VSPackage может дополнительно реализовать и который будет запрошен IDE. Когда IDE делает запрос, в свою очередь, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] попытаться получить этот интерфейс от зарегистрированного в настоящее время управления исходом VSPackage. Если интерфейс существует в зарегистрированном VSPackage, запрос IDE на пользовательские глифы удается; в противном случае [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE использует набор глифов по умолчанию.

 Метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> используется [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для получения списка изображений, показывающих различные состояния управления исходными данными. Управление исходным элементом VSPackage возвращает в IDE ручку в список изображений для своих пользовательских глифов. IDE делает копию списка изображений на данный момент и использует его позже, чтобы выбрать глифы для отображения. Если новый интерфейс не `IVsSccGlyphs::GetCustomGlyphList` поддерживается `E_NOTIMPL`или метод возвращается, то IDE получает свои глифы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]из списка глифов по умолчанию, поставляемых .

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
