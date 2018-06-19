---
title: Глиф управления (VSPackage управления источника) | Документы Microsoft
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
ms.openlocfilehash: c3787b0afad7f89743950a922d5b19c2d204bdd9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130720"
---
# <a name="glyph-control-source-control-vspackage"></a>Элемент управления глифа (VSPackage управления источника)
Тесная интеграция, доступных в систему управления версиями пакетов VSPackage входит возможность отображать собственные глифы для отображения состояния элементов системы управления версиями.  
  
## <a name="levels-of-glyph-control"></a>Уровень управления глифа  
 Глиф состояния отображается значок, который указывает текущее состояние элемента при отображении, например в **обозревателе решений** или в **представление классов**. VSPackage системы управления версиями можно обеспечить двух уровней управления глифа. Оно может ограничить выбор глифов для предварительно определенный набор глифов, предоставляемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки, или же можно определить пользовательский набор глифов для отображения.  
  
### <a name="default-set-of-glyphs"></a>Набор глифов по умолчанию  
 Чтобы определить состояние глифы, связанные с элементом в **обозревателе решений**, проект запрашивает состояние глиф из источника с помощью элемента управления <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Системы управления версиями VSPackage может быть решено оставить Выбор глифов ограничено стандартные глифы, предоставляемые интегрированной среды разработки. В этом случае пакет VSPackage обратно передает массив значений, представляющих перечисления глифов, которые определены в vsshell.idl. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Это стандартный набор глифов, задать в интегрированной среде разработки, например замка глиф «Установлен в» и флажок как глиф «Checked Out».  
  
### <a name="custom-set-of-glyphs"></a>Пользовательский набор глифов  
 VSPackage системы управления версиями можно использовать собственный глифы для уникальный «вид», при установке. Новый элемент управления источником VSPackage не активна, следует могли начать использовать свои собственные глифы даже если предыдущий источник управления VSPackage по-прежнему загружается, но неактивным. В этом режиме системы управления версиями VSPackage по-прежнему можно использовать существующие значки для обеспечения увидеть согласованы с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] по желанию его.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> Служба поддерживает интерфейс, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, которая VSPackage при необходимости можно реализовать и которого будет запрашиваться для Интегрированной средой разработки. Когда интегрированная среда разработки выполняет запрос, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] в свою очередь будет пытаться получить из системы управления версиями, зарегистрированных в настоящее время VSPackage этот интерфейс. Если интерфейс существует в зарегистрированных VSPackage, запрос интегрированной среды разработки для пользовательских глифов выполнен успешно; в противном случае [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированная среда разработки использует свой набор глифов по умолчанию.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> Используется метод [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для получения списка изображений, показывающий различные системы управления версиями состояний. В интегрированную среду разработки системы управления версиями VSPackage возвращает дескриптор для списка изображений для его пользовательских глифов. IDE создает копию списка изображений на этом этапе и использует его позже для выбора глифы для отображения. Если новый интерфейс не поддерживается или `IVsSccGlyphs::GetCustomGlyphList` метод возвращает значение E_NOTIMPL, после создания интегрированной среды разработки получает его глифов из списка по умолчанию, предоставляемые глифов [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>