---
title: "Предоставление поддержки для конструкторов &quot;Отменить&quot; | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 95e6873d0a3b254fa8f34144253a44c0a8cab60d
ms.lasthandoff: 02/22/2017

---
# <a name="supplying-undo-support-to-designers"></a>Предоставление поддержки отмены для конструкторов
Конструкторы, редакторы, как и обычно требуются для поддержки операции отмены, чтобы пользователей можно отменить их последние изменения при изменении элемента кода.  
  
 Большинство конструкторов, реализован в среде Visual Studio есть поддержка функции отмены, автоматически предоставляются средой.  
  
 Конструктор реализации, которые требуются для поддержки функции отмены:  
  
-   Обеспечивает управление отмены путем реализации абстрактного базового класса<xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>  
  
-   Введите сохраняемости и CodeDOM поддержка путем реализации <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>и <xref:System.ComponentModel.Design.IComponentChangeService>классы.</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 Дополнительные сведения о создании дизайнеры, использующие [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], в разделе [расширение поддержки времени разработки](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Предоставляет инфраструктуру отмены по умолчанию путем:  
  
-   Предоставляя отменить реализации управления через <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>и <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>классы.</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Указав сохраняемости и поддержка CodeDOM по умолчанию <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>и <xref:System.ComponentModel.Design.IComponentChangeService>реализации.</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
## <a name="obtaining-undo-support-automatically"></a>Получение поддержки отмены автоматически  
 Любые созданные в конструктор [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] поддерживает автоматическое и полной отмены if в конструкторе:  
  
-   Использует <xref:System.Windows.Forms.Control>на основе класса для пользовательского интерфейса.</xref:System.Windows.Forms.Control>  
  
-   Использует для создания кода и сохранения создания стандартного кода на основе CodeDOM и система анализа.  
  
     Дополнительные сведения о работе с поддержкой Visual Studio CodeDOM см. в разделе [динамический источник создания и компиляции кода](http://msdn.microsoft.com/Library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Когда следует использовать поддержку отмены явного конструктора  
 Конструкторы необходимо указывать управление своим отката, если они используют графический пользовательский интерфейс, называют адаптер представления, отличном от того, предоставляемые <xref:System.Windows.Forms.Control>.</xref:System.Windows.Forms.Control>  
  
 Примером этого может созданию продукта с веб-графический интерфейс, а не [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] на основе графического интерфейса.  
  
 В таких случаях необходимо зарегистрировать этот адаптер представления с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с помощью <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>и обеспечивает управление явного отката.</xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>  
  
 Конструкторы, должны предоставить CodeDOM и сохраняемости поддерживают, если они не используют [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] модели создания кода в <xref:System.CodeDom>пространства имен.</xref:System.CodeDom>  
  
## <a name="undo-support-features-of-the-designer"></a>Отменить функции поддержки конструктора  
 Пакет SDK для среды предоставляет отмены по умолчанию реализации интерфейсов, необходимых для обеспечения поддержки, который может использоваться конструкторами не используется <xref:System.Windows.Forms.Control>на основе классов для своих пользовательских интерфейсов или стандартной модели CodeDOM и сохраняемость.</xref:System.Windows.Forms.Control>  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Класс является производным от [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine>класса, используя реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>класса для управления операции отмены.</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> </xref:System.ComponentModel.Design.UndoEngine> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
 Visual Studio обеспечивает следующие функции для отмены конструктора.  
  
-   Функции отмены, связанный в нескольких конструкторах.  
  
-   Дочерних подразделениях в конструкторе можно взаимодействовать с своих родителей, реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>и <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>  
  
 Пакет SDK для среды предоставляет поддержку CodeDOM и сохраняемость, указав:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>как реализации<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
 A <xref:System.ComponentModel.Design.IComponentChangeService>предоставляемых [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'' узел разработки.</xref:System.ComponentModel.Design.IComponentChangeService>  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Использование функции пакет SDK для среды для предоставления поддержки отмены  
 Для получения поддержки отмены, реализация конструктора объекта выполните следующие действия.  
  
-   Создать и инициализировать экземпляр <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>класса является допустимым <xref:System.IServiceProvider>реализацию.</xref:System.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Это <xref:System.IServiceProvider>класс должен предоставлять следующие службы:</xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.</xref:System.ComponentModel.Design.IDesignerHost>  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         Дизайнеры, использующие [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] сериализации CodeDOM, можно использовать <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>в состав [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] реализацию <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
         В данном случае <xref:System.IServiceProvider>класс обеспечивает, <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Конструктор должен возвращать этот объект как реализация <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>класса.</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> </xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService></xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Конструкторы по умолчанию <xref:System.ComponentModel.Design.DesignSurface>предоставляемых [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] узел разработки гарантированно имеет стандартную реализацию <xref:System.ComponentModel.Design.IComponentChangeService>класса</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.DesignSurface>  
  
 Реализация конструкторов <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>механизм отмены действий на основе автоматически отслеживает изменения, если:</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Изменения свойств выполняются через <xref:System.ComponentModel.TypeDescriptor>объекта.</xref:System.ComponentModel.TypeDescriptor>  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>события создаются вручную, когда отменяемой изменение фиксируется.</xref:System.ComponentModel.Design.IComponentChangeService>  
  
-   Изменения в конструкторе был создан в контексте <xref:System.ComponentModel.Design.DesignerTransaction>.</xref:System.ComponentModel.Design.DesignerTransaction>  
  
-   Конструктор решает явно создать блоки отмены с помощью блок отмены standard, предоставляемые реализацию <xref:System.ComponentModel.Design.UndoEngine.UndoUnit>или Visual Studio конкретной реализации <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>который является производным от <xref:System.ComponentModel.Design.UndoEngine.UndoUnit>и также предоставляет реализацию для обеих <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>и <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> </xref:System.ComponentModel.Design.UndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:System.ComponentModel.Design.UndoEngine.UndoUnit>  
  
## <a name="see-also"></a>См. также  
 <xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine></xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Расширение поддержки времени разработки](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
