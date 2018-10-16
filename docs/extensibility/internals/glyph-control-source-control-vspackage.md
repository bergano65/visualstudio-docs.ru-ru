---
title: Элемент управления глифа (пакет VSPackage управления версиями) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c791647e9718686c5a6c7cf250ca84c74aabbfcc
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499254"
---
# <a name="glyph-control-source-control-vspackage"></a>Элемент управления глифа (система управления версиями. VSPackage)
Глубокая интеграция, доступных в систему управления версиями пакетов VSPackage входит возможность использовать свои собственные глифы для указания состояния элементов в системе управления версиями.  
  
## <a name="levels-of-glyph-control"></a>Уровни управления глифа  
 Глиф состояния отображается значок, который указывает текущее состояние элемента при отображении, например в **обозревателе решений** или в **представление классов**. Пакет VSPackage системы управления версиями можно использовать два уровня управления глифа. Он позволяет ограничить выбор глифов для предустановленный набор глифов, предоставляемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки, или же можно определить пользовательский набор глифов для отображения.  
  
### <a name="default-set-of-glyphs"></a>По умолчанию набор глифов  
 Чтобы определить состояние глифы, связанные с элементом в **обозревателе решений**, значок состояния из источника с помощью элемента управления для запросов проектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Элемент управления источником VSPackage может быть решено оставить Выбор глифов, ограничен стандартные глифы, предоставляемые интегрированной среды разработки. В этом случае VSPackage передает массив значений, представляющий глиф перечислений, которые определены в *vsshell.idl*. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Это стандартный набор глифов, задать в интегрированной среде разработки, например замка глифа возвращенных и флажок для извлеченных глифа.  
  
### <a name="custom-set-of-glyphs"></a>Пользовательский набор глифов  
 Пакет VSPackage системы управления версиями можно использовать свой собственный глифы для уникального внешнего вида и поведения при установке. Когда новый элемент управления источником VSPackage активен, она должна быть возможность начать использовать свой собственный глифов, даже если пакет VSPackage системы управления предыдущей версиями по-прежнему загружен, но неактивного. В этом режиме VSPackage системы управления версиями по-прежнему можете использовать существующие значки для обеспечения согласованного с взгляд [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] его желанию.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Служба поддерживает интерфейс, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, которая VSPackage при необходимости можно реализовать и которого будет запрашиваться для Интегрированной средой разработки. Когда интегрированная среда разработки выполняет запрос, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] в свою очередь будет пытаться получить из системы управления версиями, зарегистрированные на данный момент VSPackage этот интерфейс. Если интерфейс существует в зарегистрированных VSPackage, запрос IDE для пользовательских глифов выполнен успешно; в противном случае [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированная среда разработки использует его по умолчанию набор глифов.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> Используется метод [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] получить список образов, показывающий различные системы управления версиями состояний. Пакет VSPackage системы управления версиями в интегрированную среду разработки возвращает дескриптор списка изображений для его пользовательских глифов. IDE создает копию списка изображений на этом этапе и использует его позже выбрать глифы для отображения. Если новый интерфейс не поддерживается или `IVsSccGlyphs::GetCustomGlyphList` возвращает `E_NOTIMPL`, затем интегрированной среды разработки получает его глифов из списка по умолчанию глифов, предоставляемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>