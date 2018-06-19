---
title: Предоставление отмены поддержки для конструкторов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5fc289426c2560e978819efcd8eaf17e56b224a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144886"
---
# <a name="supplying-undo-support-to-designers"></a>Предоставление поддержки отмены для конструкторов
Конструкторы, редакторы, как и обычно требуется для поддержки операций отмены, чтобы пользователи могут отменить их последние изменения, при изменении элемента кода.  
  
 Большинство конструкторов, реализованные в Visual Studio имеется поддержка отмены, автоматически предоставляется средой.  
  
 Конструктора реализации, которые требуются для обеспечения поддержки функцией отмены:  
  
-   Обеспечивает управление отмены путем реализации абстрактного базового класса <xref:System.ComponentModel.Design.UndoEngine>  
  
-   Указывайте сохраняемости и CodeDOM поддержка путем реализации <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> и <xref:System.ComponentModel.Design.IComponentChangeService> классы.  
  
 Дополнительные сведения о создании с помощью конструкторов [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], в разделе [расширения поддержки времени разработки](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Предоставляет инфраструктуру отмены по умолчанию по:  
  
-   Предоставление отменить реализации управления через <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> и <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> классы.  
  
-   Указав сохраняемости и поддержка CodeDOM с помощью по умолчанию <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> и <xref:System.ComponentModel.Design.IComponentChangeService> реализации.  
  
## <a name="obtaining-undo-support-automatically"></a>Получение поддержки отмены автоматически  
 Любой конструктор, созданные в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] поддерживает автоматический, так и полного отката if в конструкторе:  
  
-   Использует <xref:System.Windows.Forms.Control> на основе класса для его пользовательского интерфейса.  
  
-   Использует стандартный код на основе CodeDOM поколения и система анализа для создания кода и сохранения.  
  
     Дополнительные сведения о работе с Visual Studio CodeDOM поддержки см. в разделе [динамического источника Создание и компиляция кода](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Когда следует использовать явное отмены конструктора  
 Конструкторы должны предоставить управление своим отката при использовании графического пользовательского интерфейса, называют адаптер представления, отличной от предоставляемых <xref:System.Windows.Forms.Control>.  
  
 Примером этого может создания продукта с помощью графического конструктора веб-интерфейса, а не [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] на основе графического интерфейса.  
  
 В таких случаях необходимо зарегистрировать этот адаптер представления с [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] с помощью <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>и обеспечить управление явного отката.  
  
 Конструкторы, должны предоставить CodeDOM и сохраняемость поддерживает, если они не используют [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] модели создания кода, приведенного в <xref:System.CodeDom> пространства имен.  
  
## <a name="undo-support-features-of-the-designer"></a>Отменить поддержку возможности конструктора  
 Пакет SDK для среды предоставляет реализации по умолчанию из интерфейсов, необходимых для обеспечения отменить поддержки, который может использоваться конструкторами не используется <xref:System.Windows.Forms.Control> на основе классов для своих пользовательских интерфейсов или стандартной модели CodeDOM и сохраняемость.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Класс является производным от [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine> класса, используя реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> класса для управления операции отмены.  
  
 Visual Studio обеспечивает следующие функции для отмены конструктора.  
  
-   Связанный откат функциональность в нескольких конструкторах.  
  
-   Дочерних подразделениях в конструкторе можно взаимодействовать с их родительских объектов, реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> на <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
 Пакет SDK для среды обеспечивает поддержку CodeDOM и сохраняемость, указав:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> как реализации <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 Объект <xref:System.ComponentModel.Design.IComponentChangeService> , предоставляемые [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'' узле разработки.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Использование функций пакета SDK среды для предоставления поддержки отмены  
 Для получения поддержки отмены, объект, реализующий конструктор должен:  
  
-   Создайте и инициализируйте экземпляр <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> класс действительным <xref:System.IServiceProvider> реализации.  
  
-   Это <xref:System.IServiceProvider> класс должен предоставлять следующие службы:  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         С помощью конструкторов [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] сериализации CodeDOM, можно использовать <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> в состав [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] в своей реализации <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
         В этом случае <xref:System.IServiceProvider> класс, предоставляемый для <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> конструктор должен возвращать этот объект как реализация <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> класса.  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Конструкторы по умолчанию <xref:System.ComponentModel.Design.DesignSurface> , предоставляемые [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] узел разработки гарантированно имеет реализацию по умолчанию <xref:System.ComponentModel.Design.IComponentChangeService> класса.  
  
 Реализация конструкторов <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> механизм отмены действий на основе автоматически отслеживает изменения, если:  
  
-   Изменения свойств выполняются через <xref:System.ComponentModel.TypeDescriptor> объекта.  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService> события создаются вручную, при изменении в отменяемом фиксации.  
  
-   Изменения в конструкторе был создан в контексте <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
-   Конструктор решает явно создать блоков отмены с помощью блок отмены standard, предоставляемые реализация <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> или Visual Studio реализацию <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, который является производным от <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> , а также предоставляет реализация обоих <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>См. также  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Расширения поддержки времени разработки](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)