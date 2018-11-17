---
title: Элемент управления глифа (пакет VSPackage управления версиями) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 820ffdd2578cc40f91d95bb489f13403c5cdecc5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772356"
---
# <a name="glyph-control-source-control-vspackage"></a>Элемент управления глифа (пакет VSPackage системы управления версиями)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Глубокая интеграция, доступных в систему управления версиями пакетов VSPackage входит возможность использовать свои собственные глифы для указания состояния элементов в системе управления версиями.  
  
## <a name="levels-of-glyph-control"></a>Уровни управления глифа  
 Глиф состояния отображается значок, который указывает текущее состояние элемента при отображении, например в **обозревателе решений** или в **представление классов**. Пакет VSPackage системы управления версиями можно использовать два уровня управления глифа. Он позволяет ограничить выбор глифов для предустановленный набор глифов, предоставляемые [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среды разработки, или же можно определить пользовательский набор глифов для отображения.  
  
### <a name="default-set-of-glyphs"></a>По умолчанию набор глифов  
 Чтобы определить состояние глифы, связанные с элементом в **обозревателе решений**, значок состояния из источника с помощью элемента управления для запросов проектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Элемент управления источником VSPackage может быть решено оставить Выбор глифов, ограничен стандартные глифы, предоставляемые интегрированной среды разработки. В этом случае VSPackage передает массив значений, представляющий глиф перечислений, которые определены в vsshell.idl. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Это стандартный набор глифов, задайте в интегрированной среде разработки, например замка для глифа «Установлен в», а метку как глиф «Checked Out».  
  
### <a name="custom-set-of-glyphs"></a>Пользовательский набор глифов  
 Пакет VSPackage системы управления версиями можно использовать свой собственный глифы для уникальный «вид» при установке. Когда новый элемент управления источником VSPackage активен, она должна быть возможность начать использовать свой собственный глифов, даже если пакет VSPackage системы управления предыдущей версиями по-прежнему загружен, но неактивного. В этом режиме VSPackage системы управления версиями по-прежнему можете использовать существующие значки для обеспечения согласованного с взгляд [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] его желанию.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Служба поддерживает интерфейс, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, которая VSPackage при необходимости можно реализовать и которого будет запрашиваться для Интегрированной средой разработки. Когда интегрированная среда разработки выполняет запрос, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] в свою очередь будет пытаться получить из системы управления версиями, зарегистрированные на данный момент VSPackage этот интерфейс. Если интерфейс существует в зарегистрированных VSPackage, запрос IDE для пользовательских глифов выполнен успешно; в противном случае [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированная среда разработки использует его по умолчанию набор глифов.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> Используется метод [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] получить список образов, показывающий различные системы управления версиями состояний. Пакет VSPackage системы управления версиями в интегрированную среду разработки возвращает дескриптор списка изображений для его пользовательских глифов. IDE создает копию списка изображений на этом этапе и использует его позже выбрать глифы для отображения. Если новый интерфейс не поддерживается или `IVsSccGlyphs::GetCustomGlyphList` метод возвращает E_NOTIMPL, затем интегрированной среды разработки получает его глифов из списка по умолчанию глифов, предоставляемые [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

