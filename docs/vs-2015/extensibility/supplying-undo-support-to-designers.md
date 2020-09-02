---
title: Предоставление поддержки отмены для конструкторов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6136caaec0cb8f0d79e3fb7b96245fc3fd070710
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675343"
---
# <a name="supplying-undo-support-to-designers"></a>Предоставление поддержки команды отмены для конструкторов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Конструкторам, например редакторам, обычно требуется поддержка операций отмены, чтобы пользователи могли обратить свои последние изменения при изменении элемента кода.  
  
 Большинство конструкторов, реализованных в Visual Studio, поддерживают отмену, автоматически предоставляемую средой.  
  
 Реализации конструктора, которые должны обеспечивать поддержку функции отмены:  
  
- Обеспечение управления отменой путем реализации абстрактного базового класса <xref:System.ComponentModel.Design.UndoEngine>  
  
- Предоставьте поддержку сохраняемости и CodeDOM, реализовав <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> классы и.  
  
  Дополнительные сведения о создании конструкторов с помощью [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] см. в разделе [расширение поддержки времени разработки](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Предоставляет инфраструктуру отмены по умолчанию:  
  
- Предоставление реализации управления отменой с помощью <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> классов и.  
  
- Предоставление поддержки сохраняемости и CodeDOM с помощью реализаций по умолчанию <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> и <xref:System.ComponentModel.Design.IComponentChangeService> .  
  
## <a name="obtaining-undo-support-automatically"></a>Автоматическое получение поддержки отмены  
 Любой конструктор, созданный в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , поддерживает автоматическую и полную отменяемую поддержку, если конструктор:  
  
- Использует <xref:System.Windows.Forms.Control> класс на основе пользовательского интерфейса.  
  
- Использует стандартную систему создания и анализа кода на основе CodeDOM для создания и сохранения кода.  
  
     Дополнительные сведения о работе с поддержкой Visual Studio CodeDOM см. в разделе [Динамическое создание и компиляция исходного кода](https://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb) .  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Когда следует использовать явную поддержку отмены конструктора  
 Конструкторы должны предоставлять собственные способы отмены, если они используют графический пользовательский интерфейс, который называется адаптером представления, отличным от интерфейса, предоставленного <xref:System.Windows.Forms.Control> .  
  
 Примером этого может быть создание продукта с помощью веб-интерфейса графического дизайна, а не [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] графического интерфейса на основе.  
  
 В таких случаях необходимо зарегистрировать этот адаптер представления с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] помощью <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> и предоставить явное управление отменой.  
  
 Конструкторам необходимо предоставить поддержку CodeDOM и сохраняемости, если они не используют [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] модель создания кода, указанную в <xref:System.CodeDom> пространстве имен.  
  
## <a name="undo-support-features-of-the-designer"></a>Отмена поддержки функций конструктора  
 Пакет SDK для среды предоставляет реализации по умолчанию интерфейсов, необходимых для обеспечения поддержки отмены, которые могут использоваться конструкторами, не использующими <xref:System.Windows.Forms.Control> классы на основе для своих пользовательских интерфейсов или стандартных моделей CodeDOM и модели сохраняемости.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Класс является производным от [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> класса, использующего реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> класса для управления операциями отмены.  
  
 Visual Studio предоставляет следующие возможности для отмены конструктора:  
  
- Связанные функции отмены в нескольких конструкторах.  
  
- Дочерние элементы в конструкторе могут взаимодействовать с их родителями путем реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> включения <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .  
  
  Пакет SDK для среды предоставляет поддержку CodeDOM и сохраняемости, предоставляя:  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> как реализации <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  Объект, <xref:System.ComponentModel.Design.IComponentChangeService> предоставленный [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] узлом разработки "".  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Использование функций пакета SDK среды для предоставления поддержки отмены  
 Чтобы получить поддержку отмены, объект, реализующий конструктор, должен:  
  
- Создайте экземпляр класса и инициализируйте его <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> с помощью допустимой <xref:System.IServiceProvider> реализации.  
  
- Этот <xref:System.IServiceProvider> класс должен предоставлять следующие службы:  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       Конструкторы, использующие [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] сериализацию CodeDOM, могут использовать <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> предоставленный в [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] качестве его реализации <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .  
  
       В этом случае класс, <xref:System.IServiceProvider> предоставленный <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> конструктору, должен возвращать этот объект как реализацию <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> класса.  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       Конструкторы, использующие по умолчанию, <xref:System.ComponentModel.Design.DesignSurface> предоставляемые [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] узлом разработки, гарантированно имеют реализацию класса по умолчанию <xref:System.ComponentModel.Design.IComponentChangeService> .  
  
  Конструкторы, реализующие <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> механизм отмены на основе, автоматически отслеживают изменения, если:  
  
- Изменения свойств вносятся через <xref:System.ComponentModel.TypeDescriptor> объект.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> события создаются вручную при фиксации изменения, которое может быть отменено.  
  
- Изменение в конструкторе было создано в контексте <xref:System.ComponentModel.Design.DesignerTransaction> .  
  
- Конструктор выбирает явное создание блоков отмены с помощью стандартной единицы отмены, предоставляемой реализацией <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> , или реализации, относящейся к Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> , которая является производной от класса, <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> а также предоставляет реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .  
  
## <a name="see-also"></a>См. также:  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Расширения поддержки времени разработки](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
