---
title: Предоставление поддержки для конструкторов "Отменить" | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc17f59858637048c12929411a0f413ed625ad10
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331631"
---
# <a name="supply-undo-support-to-designers"></a>Поддержка функции отмены поставок для конструкторов

Конструкторы, таких как редакторы, обычно требуется для поддержки отмены операций, таким образом, пользователи могут отменить их последние изменения, при изменении элемента кода.

Большинство конструкторов, реализованные в Visual Studio имеют «отмены» автоматически предоставляемых средой поддержки.

Реализации конструктора, которым требуется, чтобы обеспечить поддержку функции отмены:

- Задать механизмы управления отменой, можно реализовать абстрактный базовый класс <xref:System.ComponentModel.Design.UndoEngine>

- Укажите сохраняемость и CodeDOM поддержка путем реализации <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> и <xref:System.ComponentModel.Design.IComponentChangeService> классы.

Дополнительные сведения о создании дизайнеры, использующие [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], см. в разделе [расширить поддержку времени разработки](/previous-versions/37899azc(v=vs.140)).

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Предоставляет инфраструктуру отмены по умолчанию путем:

- Предоставляя отменить реализации управления посредством <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> и <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> классы.

- Указав сохраняемости и поддержка CodeDOM через значение по умолчанию <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> и <xref:System.ComponentModel.Design.IComponentChangeService> реализаций.

## <a name="obtain-undo-support-automatically"></a>Автоматическое получение поддержка функции отмены

Любого конструктора, созданных в Visual Studio имеет возможность отмены изменений автоматического и полного if, конструкторе:

- Использует <xref:System.Windows.Forms.Control> на основе класса для пользовательского интерфейса.

- Использует стандартный код на основе модели CodeDOM поколения и система анализа для создания кода и сохранения.

   Дополнительные сведения о работе с поддержкой Visual Studio CodeDOM см. в разделе [динамического кода Создание и компиляция исходного](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Когда следует использовать явные конструктора отмены поддержки
 Конструкторы необходимо указывать свои собственные механизмы управления отменой, если они используют графический пользовательский интерфейс, называется адаптер представления, отличной от предоставляемых <xref:System.Windows.Forms.Control>.

 Примером этого может созданию продукта с существует веб-графический интерфейс, а не [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-на основе графического интерфейса.

 В таком случае необходимо зарегистрировать этот адаптер представления с помощью Visual Studio с помощью <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>и обеспечивает управление явного отката.

 Необходимо предоставить CodeDOM и сохраняемости поддержки, если они не используют модели создания кода Visual Studio, в конструкторы <xref:System.CodeDom> пространства имен.

## <a name="undo-support-features-of-the-designer"></a>Отменить функции поддержки конструктора
 Пакет SDK для среды предоставляет реализации по умолчанию интерфейсов, необходимых для обеспечения отмены поддержки, который может использоваться конструкторами неиспользование <xref:System.Windows.Forms.Control> основе классы для их пользовательские интерфейсы или стандартную модель CodeDOM и сохраняемость.

 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Класс является производным от [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine> класса, используя реализацию <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> класса для управления операции отмены.

 Visual Studio предоставляет следующие функции для отмены конструктора:

- Функциональные возможности связанный откат несколько конструкторов.

- Дочерние единицы в конструкторе можно взаимодействовать с их родительские элементы путем реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> на <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.

Пакет SDK для среды обеспечивает поддержку CodeDOM и постоянного хранения, указав:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> как реализации <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Объект <xref:System.ComponentModel.Design.IComponentChangeService> предоставляется узлом разработки Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Используйте функции пакета SDK для окружения для предоставления поддержки отмены

Чтобы получить возможность отмены изменений, объект, реализующий конструктор необходимо создать и инициализировать экземпляр <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> класса является допустимым <xref:System.IServiceProvider> реализации. Это <xref:System.IServiceProvider> класс должен предоставлять следующие службы:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Дизайнеры, использующие сериализации Visual Studio CodeDOM можете использовать <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> в состав [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] его реализацию <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.

   В этом случае <xref:System.IServiceProvider> класс, предоставляемый для <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> конструктор должен возвращать этот объект как реализация <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> класса.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Конструкторы по умолчанию <xref:System.ComponentModel.Design.DesignSurface> предоставляемых структурой в Visual Studio узел всегда имеют реализацию по умолчанию <xref:System.ComponentModel.Design.IComponentChangeService> класса.

Реализация конструкторов <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> механизм отмены действий на основе автоматически отслеживает изменения, если:

- Изменения свойств выполняются через <xref:System.ComponentModel.TypeDescriptor> объекта.

- <xref:System.ComponentModel.Design.IComponentChangeService> события создаются вручную в том случае, когда отменяемое изменение фиксируется.

- Изменения в конструкторе был создан в контексте <xref:System.ComponentModel.Design.DesignerTransaction>.

- Конструктор выбирает для явного создания блоков отмены, с помощью стандартных отмены, предоставляемые реализацию <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> или Visual Studio реализация <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, который является производным от <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> , а также предоставляет реализация обоих <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> и <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.

## <a name="see-also"></a>См. также

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Расширения поддержки времени разработки](/previous-versions/37899azc(v=vs.140))