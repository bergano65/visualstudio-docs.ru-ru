---
title: Управление панелью элементов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox [Visual Studio SDK], automatic tab selection
- Toolbox [Visual Studio SDK], managing
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: ba4b166cc409dd2c50c258a9b82ee34c22e9b084
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838687"
---
# <a name="managing-the-toolbox"></a>Managing the Toolbox
[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] позволяет пакету VSPackage, например редактору или конструктору, управлять членством и внешним видом **панели элементов**.  
  
 Кроме того, с помощью средств автоматизации можно управлять самой **панелью элементов** . Дополнительные сведения об управлении панелью элементов посредством автоматизации см. в разделе [как: Control the Toolbox](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599).  
  
## <a name="automatic-toolbox-tab-selection"></a>Автоматический выбор вкладок панели элементов  
 Определенная вкладка или категория **панели элементов** может активироваться автоматически в соответствии с активным в настоящий момент редактором или конструктором. Например, при активации конструктора форм может быть необходимо, чтобы была выбрана вкладка **Все формы Windows Forms** .  
  
 Эта поддержка ограничена редакторами и конструкторами, которые требуют следующего:  
  
1. реализации объекта фабрики для предоставления экземпляров редактора или конструктора (дополнительные сведения о реализации объекта фабрики конструктора или редактора см. в разделе [Editor Factories](../extensibility/editor-factories.md));  
  
2. регистрации вкладки панели элементов, которая автоматически активируется при наличии редактора или конструктора.  
  
## <a name="controlling-the-toolbox"></a>Управление панелью элементов  
 Помимо поддержки автоматизации [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] предоставляет указанные ниже интерфейсы для расширения возможностей пакетов VSPackage по управлению **панелью элементов** .  
  
|Интерфейс|Описание|  
|---------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|Позволяет приложениям управлять ими, добавлять и удалять <xref:System.Drawing.Design.ToolboxItem> объектов из **элементов**. Также позволяет настраивать внешний вид и категории **панели элементов** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Позволяет приложениям добавлять и удалять активные элементы управления **панели элементов** , управлять ими, а также настраивать внешний вид и категории **панели элементов** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|Расширяет функциональные возможности <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>, предоставляя полную поддержку сохраняемости и локализации.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 При работе с этими интерфейсами важно учитывать ряд важных моментов.  
  
- <xref:System.Drawing.Design.IToolboxService> доступен только пакетам VSPackage на основе Managed Package Framework.  
  
- Добавлять элементы управления не может напрямую **элементов** с помощью <xref:System.Drawing.Design.IToolboxService>.  
  
- Пакет VSPackage должен использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> для добавления элементов управления или размещать элемент управления в элементе управления-оболочке, производной от <xref:System.Windows.Forms.AxHost>.  
  
   Visual Studio предоставляет средство `Aximp.exe` для автоматизации инкапсуляции элемента ActiveX в элементе управления, производном от <xref:System.Windows.Forms.AxHost>. Дополнительные сведения см. в разделе [Aximp.exe (Windows Forms ActiveX программа импорта элементов)](http://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0).  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> — это интерфейсы на базе COM, доступные через сборки взаимодействия.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> является производным от <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> и реализует все его методы.  
  
   Объекты получают только экземпляр <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> не является производным от <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> и не реализует его методы.  
  
   Объекты, которым требуются функциональные возможности обоих интерфейсов, должны получить их экземпляры из среды.  
  
- При работе с <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> сведения о канонических (нелокализованных) именах вкладок обрабатываются методами <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A>.  
  
- При использовании <xref:System.Drawing.Design.IToolboxService> управление локализованными сведениями, например именами категорий, осуществляется разработчиком.  
  
  Чтобы разрешить пользователям сохранять параметры **панели элементов** , доступ к которым они получают с помощью команды **Импорт и экспорт параметров** в меню **Сервис** интегрированной среды разработки, используйте механизм параметров. Дополнительные сведения об использовании параметров см. в разделе [Extending User Settings and Options](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="see-also"></a>См. также  
 [Расширение панели элементов](../misc/extending-the-toolbox.md)